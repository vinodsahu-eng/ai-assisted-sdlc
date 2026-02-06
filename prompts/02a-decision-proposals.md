# Product Decision Proposals (Phase 2A)

**Technical Product Owner:** Principal Engineering Review  
**Created:** February 6, 2026  
**Status:** PROPOSALS ONLY - No Decisions Made  

---

## Executive Summary

This document proposes product options for four blocking ambiguities identified in the SkyHigh Core domain analysis. These proposals require stakeholder decision before PRD creation can proceed.

**⚠️ CRITICAL:** All items below are PROPOSALS, not decisions. No work should proceed without explicit stakeholder approval of selected options.

---

## 1. Waitlist Ordering Logic

**Current Ambiguity:** The domain context specifies "next eligible waitlisted passenger" but does not define eligibility or ordering criteria.

### Option A: First-Come, First-Served (FCFS)
**Behavior:** Passengers are served in order of waitlist join timestamp.
- Simple, predictable, fair to all passengers
- Easy to explain and validate
- No passenger classification required

**Trade-offs:**
- Ignores business value differentiation (premium vs economy passengers)  
- No accommodation for operational priorities
- May not optimize revenue

### Option B: Fare Class Priority with FCFS Tiebreaker  
**Behavior:** Priority queue ordered by fare class, then join timestamp within each class.
- Business/First class passengers served before Economy
- Maintains fairness within fare classes  
- Aligns with airline revenue optimization

**Trade-offs:**  
- Requires fare class information integration
- More complex logic and edge cases
- Potential customer satisfaction issues for economy passengers

### Option C: Dynamic Priority Scoring
**Behavior:** Weighted scoring based on multiple factors (fare class, loyalty status, check-in urgency).
- Maximum flexibility for business rules
- Can optimize multiple business objectives

**Trade-offs:**
- Most complex to implement and maintain  
- Difficult to explain to passengers
- Potential for gaming/manipulation

### **Recommended Option: A (FCFS)**
**Rationale:** Provides fairness, predictability, and simplicity. Can be enhanced later if business requirements emerge for passenger prioritization. Minimizes implementation risk while ensuring functional completeness.

---

## 2. Abuse Detection Threshold Authority  

**Current Ambiguity:** Problem statement provides example (50 seat maps in 2 seconds) but unclear whether this is authoritative rule or illustration.

### Option A: Fixed Authoritative Thresholds
**Behavior:** Treat example thresholds as definitive business rules.
- 50 requests per 2-second window triggers restriction
- Thresholds are hard-coded business constants
- Clear, unambiguous behavior

**Trade-offs:**
- Cannot adapt to changing attack patterns
- May be too restrictive for legitimate use cases
- Requires code changes to adjust thresholds

### Option B: Configurable Business Rules
**Behavior:** Thresholds are configurable parameters managed by business operations.
- Initial defaults based on problem statement examples  
- Business can adjust based on operational experience
- Different thresholds for different abuse patterns

**Trade-offs:**
- Requires configuration management capability
- Risk of misconfiguration causing false positives
- Additional operational complexity

### Option C: Adaptive Detection System
**Behavior:** System learns normal patterns and dynamically adjusts thresholds.
- Machine learning approach to abuse detection
- Automatically adapts to traffic patterns
- Can detect new abuse types

**Trade-offs:**
- Significant complexity and development time
- Black-box behavior difficult to audit
- May have learning period with suboptimal detection

### **Recommended Option: B (Configurable Business Rules)**
**Rationale:** Balances implementation simplicity with operational flexibility. Allows business to refine thresholds based on real-world experience without code changes. Provides clear audit trail for threshold decisions.

---

## 3. Restriction Behavior & Duration

**Current Ambiguity:** When abuse is detected, the domain specifies "restrict or block further access temporarily" but doesn't define duration, scope, or specific behavior.

### Option A: Simple Time-Based Block
**Behavior:** Complete access block for fixed duration (e.g., 15 minutes).
- Block all requests from detected source
- Fixed duration from detection time
- Simple binary restriction state

**Trade-offs:**
- May be too harsh for accidental triggering
- No graduated response to different severity levels  
- Potential impact to legitimate concurrent users from same IP

### Option B: Graduated Response System  
**Behavior:** Escalating restrictions based on abuse severity and history.
- First offense: Rate limiting (reduced allowed requests)
- Repeat offenses: Temporary blocks with increasing duration
- Severe abuse: Extended blocks

**Trade-offs:**
- More complex state management required
- Multiple restriction levels to define and maintain
- Requires historical tracking of abuse incidents

### Option C: Functional Restriction with Appeal
**Behavior:** Block specific high-risk functions while allowing basic operations.
- Block seat selection/holding capabilities  
- Allow read-only seat map viewing
- Manual review/appeal process for false positives

**Trade-offs:**
- Most complex to implement correctly
- Requires classification of request types
- Manual review process adds operational overhead

### **Recommended Option: A (Simple Time-Based Block)**  
**Rationale:** Provides clear, auditable protection with minimal implementation complexity. 15-minute duration balances protection against legitimate user inconvenience. Can be enhanced with graduated responses in future iterations if needed.

---

## 4. Concurrent / Group Seat Holds

**Current Ambiguity:** Domain allows single passenger to hold one seat, but unclear if passengers can hold multiple seats concurrently or how group check-ins should behave.

### Option A: Single Seat Limit Per Passenger
**Behavior:** Each passenger can hold maximum one seat at any time.
- Must complete or cancel current hold before selecting another
- Group check-ins require sequential individual check-ins
- Simple hold management

**Trade-offs:**  
- Poor user experience for group travelers
- No support for families checking in together
- May increase seat conflicts for groups

### Option B: Limited Multi-Seat Holds Per Passenger
**Behavior:** Passengers can hold up to N seats simultaneously (e.g., 4 seats).
- Suitable for family/small group check-ins
- All holds share same 120-second expiry from first selection
- Passenger must complete all held seats together

**Trade-offs:**
- More complex hold management and expiry logic
- Potential for increased seat hoarding  
- Requires group size limits and enforcement

### Option C: Group Check-In Entity
**Behavior:** Separate group check-in process for multiple passengers.
- Group leader initiates multi-passenger check-in
- Can hold seats for all group members simultaneously
- Group-specific business rules and limits

**Trade-offs:**
- Requires new domain entity (Group) and associated complexity
- Authentication and authorization for group operations  
- Significant expansion of domain scope

### **Recommended Option: B (Limited Multi-Seat Holds)**
**Rationale:** Balances user experience for legitimate group travel against abuse potential. 4-seat limit covers majority of family travel while preventing large-scale hoarding. Reuses existing hold mechanisms with manageable complexity additions.

---

## Implementation Readiness Assessment  

Based on these recommendations, the system would have:

✅ **Clear business rules** for all major ambiguities  
✅ **Manageable implementation complexity** for MVP
✅ **Room for enhancement** in future iterations
✅ **Auditability** of all business decisions

## Next Steps

1. **Stakeholder review** of all proposed options
2. **Explicit approval** of selected options for each ambiguity  
3. **PRD creation** incorporating approved decisions
4. **Domain context update** with resolved ambiguities

---

**STOP CONDITION REACHED**  
**Awaiting stakeholder decision on proposed options before proceeding to PRD creation.**
