# Decision Frameworks & Templates

**Last Updated**: [Date]  
**Review Frequency**: Quarterly  
**Active Decisions**: [X] in process

---

## 🎯 What Are Decision Frameworks?

Decision frameworks provide structured approaches to making consistent, high-quality technology decisions. They help reduce bias, ensure thorough analysis, and document rationale for future reference.

---

## 📋 Framework Index

### Decision Types & Frameworks
| Decision Type | Framework | Complexity | Stakeholders | Risk Level |
|---------------|------------|-------------|--------------|------------|
| **Technology Selection** | [Framework name] | Low/Med/High | [Roles] | Low/Med/High |
| **Architecture Changes** | [Framework name] | Low/Med/High | [Roles] | Low/Med/High |
| **Hiring Decisions** | [Framework name] | Low/Med/High | [Roles] | Low/Med/High |
| **Investment Decisions** | [Framework name] | Low/Med/High | [Roles] | Low/Med/High |
| **Risk Management** | [Framework name] | Low/Med/High | [Roles] | Low/Med/High |

---

## 🛠️ Technology Selection Framework

### TECH-SELECT: Technology Evaluation Framework

#### 1. Business Alignment Assessment
| Question | Weight | Score (1-10) | Weighted Score |
|----------|--------|---------------|----------------|
| **Does this technology solve a real business problem?** | [X]% | [Score] | [Result] |
| **Will this technology create competitive advantage?** | [X]% | [Score] | [Result] |
| **Is the timing right for this investment?** | [X]% | [Score] | [Result] |
| **Does this align with our 3-year strategy?** | [X]% | [Score] | [Result] |

#### 2. Technical Evaluation
| Criterion | Weight | Score (1-10) | Weighted Score | Notes |
|-----------|--------|---------------|----------------|-------|
| **Performance & Scalability** | [X]% | [Score] | [Result] | [Notes] |
| **Integration Complexity** | [X]% | [Score] | [Result] | [Notes] |
| **Security & Compliance** | [X]% | [Score] | [Result] | [Notes] |
| **Maintainability** | [X]% | [Score] | [Result] | [Notes] |
| **Reliability & Stability** | [X]% | [Score] | [Result] | [Notes] |

#### 3. Team & Organizational Impact
| Factor | Weight | Score (1-10) | Weighted Score | Mitigation |
|---------|--------|---------------|----------------|------------|
| **Team Learning Curve** | [X]% | [Score] | [Result] | [Mitigation] |
| **Talent Availability** | [X]% | [Score] | [Result] | [Mitigation] |
| **Community Support** | [X]% | [Score] | [Result] | [Mitigation] |
| **Vendor Lock-in Risk** | [X]% | [Score] | [Result] | [Mitigation] |

#### 4. Financial Analysis
| Factor | Calculation | Result | Assessment |
|---------|-------------|---------|------------|
| **Total Cost of Ownership (3 years)** | [Calculation] | [$] | [Assessment] |
| **Implementation Cost** | [Calculation] | [$] | [Assessment] |
| **Expected ROI** | [Calculation] | [X]X | [Assessment] |
| **Payback Period** | [Calculation] | [X] months | [Assessment] |

#### 5. Risk Assessment
| Risk Type | Probability | Impact | Risk Score | Mitigation Strategy |
|------------|-------------|---------|------------|-------------------|
| **Technical Risk** | [Low/Med/High] | [Low/Med/High] | [Score] | [Strategy] |
| **Business Risk** | [Low/Med/High] | [Low/Med/High] | [Score] | [Strategy] |
| **Financial Risk** | [Low/Med/High] | [Low/Med/High] | [Score] | [Strategy] |
| **Operational Risk** | [Low/Med/High] | [Low/Med/High] | [Score] | [Strategy] |

### Decision Scoring Matrix
| Technology | Business Score | Technical Score | Team Score | Financial Score | Risk Score | Overall |
|------------|---------------|----------------|-------------|-----------------|------------|---------|
| **[Option 1]** | [Score] | [Score] | [Score] | [Score] | [Score] | **[Total]** |
| **[Option 2]** | [Score] | [Score] | [Score] | [Score] | [Score] | **[Total]** |
| **[Option 3]** | [Score] | [Score] | [Score] | [Score] | [Score] | **[Total]** |

---

## 🏗️ Architecture Decision Framework

### ARCH-DECIDE: Architecture Decision Framework

#### 1. Context Analysis
**Problem Statement**: [Clear description of the architectural problem]

**Current State**: 
- [Current architecture description]
- [Current pain points and limitations]
- [Performance and scale constraints]

**Future Requirements**:
- [Functional requirements]
- [Non-functional requirements]
- [Scale and performance requirements]
- [Security and compliance requirements]

#### 2. Stakeholder Impact Analysis
| Stakeholder | Impact | Concerns | Requirements | Commitment Needed |
|-------------|---------|-----------|--------------|------------------|
| **Engineering Team** | [Impact level] | [Concerns] | [Requirements] | [What's needed] |
| **Product Team** | [Impact level] | [Concerns] | [Requirements] | [What's needed] |
| **Operations Team** | [Impact level] | [Concerns] | [Requirements] | [What's needed] |
| **Security Team** | [Impact level] | [Concerns] | [Requirements] | [What's needed] |
| **Business** | [Impact level] | [Concerns] | [Requirements] | [What's needed] |

#### 3. Alternative Analysis
| Alternative | Pros | Cons | Implementation Complexity | Risk Level |
|-------------|-------|------|------------------------|------------|
| **Option 1: [Name]** | [Pros] | [Cons] | [Complexity] | [Risk] |
| **Option 2: [Name]** | [Pros] | [Cons] | [Complexity] | [Risk] |
| **Option 3: [Name]** | [Pros] | [Cons] | [Complexity] | [Risk] |

#### 4. Decision Criteria Scoring
| Criterion | Weight | Option 1 | Option 2 | Option 3 |
|-----------|--------|----------|----------|----------|
| **Scalability** | [X]% | [Score] | [Score] | [Score] |
| **Maintainability** | [X]% | [Score] | [Score] | [Score] |
| **Security** | [X]% | [Score] | [Score] | [Score] |
| **Performance** | [X]% | [Score] | [Score] | [Score] |
| **Cost** | [X]% | [Score] | [Score] | [Score] |
| **Implementation Time** | [X]% | [Score] | [Score] | [Score] |
| **Team Adoption** | [X]% | [Score] | [Score] | [Score] |
| **Total Score** | 100% | **[Total]** | **[Total]** | **[Total]** |

#### 5. Implementation Planning
**Chosen Alternative**: [Selected option]

**Implementation Phases**:
- **Phase 1**: [Description] - [Timeline] - [Owner] - [Success criteria]
- **Phase 2**: [Description] - [Timeline] - [Owner] - [Success criteria]
- **Phase 3**: [Description] - [Timeline] - [Owner] - [Success criteria]

**Resource Requirements**:
- **Team**: [People needed] - [Timeline]
- **Budget**: [Amount needed] - [Breakdown]
- **External Resources**: [Vendors/consultants] - [Cost]

**Risk Mitigation**:
- **Primary Risk**: [Risk] - [Mitigation] - [Owner]
- **Secondary Risk**: [Risk] - [Mitigation] - [Owner]

---

## 👥 Hiring Decision Framework

### HIRE-SCORE: Hiring Evaluation Framework

#### 1. Role Requirements Analysis
**Critical Success Factors**:
1. **[Factor 1]**: [Description] - Weight: [X]%
2. **[Factor 2]**: [Description] - Weight: [X]%
3. **[Factor 3]**: [Description] - Weight: [X]%
4. **[Factor 4]**: [Description] - Weight: [X]%

#### 2. Candidate Evaluation Matrix
| Candidate | Technical Skills | Experience | Culture Fit | Leadership | Learning Ability | Communication | Total |
|-----------|-----------------|-----------|-------------|------------|-----------------|--------------|--------|
| **[Name 1]** | [Score] | [Score] | [Score] | [Score] | [Score] | [Score] | **[Total]** |
| **[Name 2]** | [Score] | [Score] | [Score] | [Score] | [Score] | [Score] | **[Total]** |
| **[Name 3]** | [Score] | [Score] | [Score] | [Score] | [Score] | [Score] | **[Total]** |

#### 3. Risk Assessment for Final Candidates
| Risk Factor | Candidate 1 | Candidate 2 | Candidate 3 | Mitigation |
|-------------|-------------|-------------|-------------|------------|
| **Technical Overestimation** | [Risk level] | [Risk level] | [Risk level] | [Mitigation] |
| **Culture Fit** | [Risk level] | [Risk level] | [Risk level] | [Mitigation] |
| **Retention Risk** | [Risk level] | [Risk level] | [Risk level] | [Mitigation] |
| **Compensation Expectations** | [Risk level] | [Risk level] | [Risk level] | [Mitigation] |

#### 4. Decision Rationale Template
**Selected Candidate**: [Name]

**Key Strengths**:
1. **[Strength 1]**: [Evidence from interviews]
2. **[Strength 2]**: [Evidence from interviews]
3. **[Strength 3]**: [Evidence from interviews]

**Potential Concerns & Mitigation**:
1. **[Concern 1]**: [Mitigation strategy]
2. **[Concern 2]**: [Mitigation strategy]

**Long-term Potential**: [Assessment of growth trajectory]

---

## 💰 Investment Decision Framework

### INVEST-ROI: Investment Decision Framework

#### 1. Strategic Alignment
| Strategic Goal | Alignment Level | Impact | Confidence |
|----------------|----------------|---------|-------------|
| **[Goal 1]** | [High/Med/Low] | [Impact description] | [High/Med/Low] |
| **[Goal 2]** | [High/Med/Low] | [Impact description] | [High/Med/Low] |

#### 2. Financial Analysis
| Metric | Calculation | Result | Benchmark |
|--------|-------------|---------|-----------|
| **Net Present Value (NPV)** | [Formula] | [$] | [Benchmark] |
| **Internal Rate of Return (IRR)** | [Formula] | [X]% | [Benchmark] |
| **Payback Period** | [Formula] | [X] years | [Benchmark] |
| **Return on Investment (ROI)** | [Formula] | [X]X | [Benchmark] |

#### 3. Risk-Adjusted Return
| Risk Category | Probability | Impact | Expected Loss | Risk Reduction Cost |
|---------------|-------------|---------|---------------|-------------------|
| **Market Risk** | [X]% | [$] | [$] | [$] |
| **Technology Risk** | [X]% | [$] | [$] | [$] |
| **Execution Risk** | [X]% | [$] | [$] | [$] |
| **Competitive Risk** | [X]% | [$] | [$] | [$] |

**Risk-Adjusted ROI**: [Calculation] = [X]X

#### 4. Portfolio Analysis
| Investment | Amount | Expected Return | Risk Level | Portfolio Contribution |
|-------------|--------|----------------|------------|---------------------|
| **[Investment 1]** | [$] | [X]X | [Risk] | [Contribution] |
| **[Investment 2]** | [$] | [X]X | [Risk] | [Contribution] |
| **[Investment 3]** | [$] | [X]X | [Risk] | [Contribution] |

---

## 🚨 Crisis Decision Framework

### CRISIS-RESPONSE: Crisis Management Framework

#### 1. Immediate Assessment (First 15 Minutes)
| Factor | Assessment | Impact | Urgency |
|---------|------------|--------|---------|
| **Customer Impact** | [Assessment] | [Impact level] | [Urgency] |
| **Revenue Impact** | [Assessment] | [Impact level] | [Urgency] |
| **Reputation Impact** | [Assessment] | [Impact level] | [Urgency] |
| **Legal/Regulatory Impact** | [Assessment] | [Impact level] | [Urgency] |

#### 2. Response Options
| Option | Speed | Effectiveness | Cost | Risk |
|--------|-------|--------------|------|------|
| **Immediate Fix** | [Speed] | [Effectiveness] | [Cost] | [Risk] |
| **Temporary Workaround** | [Speed] | [Effectiveness] | [Cost] | [Risk] |
| **Full System Rollback** | [Speed] | [Effectiveness] | [Cost] | [Risk] |
| **Status Quo** | [Speed] | [Effectiveness] | [Cost] | [Risk] |

#### 3. Communication Strategy
| Audience | Message | Channel | Timing | Owner |
|----------|---------|----------|--------|-------|
| **Customers** | [Message] | [Channel] | [Timing] | [Owner] |
| **Employees** | [Message] | [Channel] | [Timing] | [Owner] |
| **Management** | [Message] | [Channel] | [Timing] | [Owner] |
| **Board** | [Message] | [Channel] | [Timing] | [Owner] |
| **Media/Public** | [Message] | [Channel] | [Timing] | [Owner] |

#### 4. Post-Crisis Learning
| Category | What Happened | Root Cause | Lessons Learned | Prevention |
|-----------|--------------|------------|----------------|------------|
| **Technical** | [Description] | [Cause] | [Learning] | [Prevention] |
| **Process** | [Description] | [Cause] | [Learning] | [Prevention] |
| **Communication** | [Description] | [Cause] | [Learning] | [Prevention] |

---

## 📊 Decision Quality Framework

### DECISION-QUALITY: Decision Assessment Framework

#### Six Elements of Quality Decision
| Element | Assessment Score (1-10) | Evidence | Improvement Actions |
|----------|-----------------------|----------|--------------------|
| **Appropriate Frame** | [Score] | [Evidence of proper framing] | [Actions] |
| **Creative Alternatives** | [Score] | [Evidence of exploring options] | [Actions] |
| **Relevant Information** | [Score] | [Evidence of sufficient research] | [Actions] |
| **Clear Values & Tradeoffs** | [Score] | [Evidence of clear criteria] | [Actions] |
| **Logically Correct Reasoning** | [Score] | [Evidence of sound analysis] | [Actions] |
| **Commitment to Action** | [Score] | [Evidence of implementation readiness] | [Actions] |

**Overall Decision Quality Score**: **[Score]/10**

---

## 🔄 Decision Log Template

### Decision Entry Template

**Decision ID**: DEC-[YYYY-MM-DD]-[XXX]  
**Date**: [Date]  
**Decision Type**: [Technology/Architecture/Hiring/Investment/Crisis]  
**Status**: [In Progress/Implemented/Rejected/Deferred]  
**Impact Level**: [High/Medium/Low]

---

#### Decision Statement
**Title**: [Brief, clear title]
**Description**: [One-paragraph summary of what was decided]

#### Context & Problem
**Problem Statement**: [Clear description of the problem]
**Urgency**: [Timeline/Pressure for decision]
**Stakeholders**: [Who is affected]
**Constraints**: [Budget, time, resource constraints]

#### Decision Process
**Framework Used**: [Which framework was applied]
**Options Considered**: [List of alternatives evaluated]
**Consultation**: [Who was consulted]
**Decision Maker**: [Who made final decision]

#### Decision Made
**Choice**: [What was selected]
**Rationale**: [Key reasons for this choice]
**Key Tradeoffs**: [What was given up]
**Implementation Date**: [When decision takes effect]

#### Expected Outcomes
**Primary Benefits**: [Expected positive outcomes]
**Potential Downsides**: [Known negative consequences]
**Success Metrics**: [How we'll measure success]
**Timeline for Results**: [When to expect outcomes]

#### Implementation Plan
**Owner**: [Who is responsible for implementation]
**Key Milestones**: [Major implementation steps]
**Resource Requirements**: [What's needed to implement]
**Monitoring**: [How implementation will be tracked]

---

## 📈 Decision Analysis & Learning

### Quarterly Decision Review

#### Decision Effectiveness Analysis
| Decision ID | Expected Outcome | Actual Outcome | Success Rate | Learning |
|-------------|-----------------|----------------|--------------|----------|
| **DEC-[ID]** | [Expected] | [Actual] | [X]% | [Learning] |
| **DEC-[ID]** | [Expected] | [Actual] | [X]% | [Learning] |

#### Decision Quality Improvement
| Quality Element | Average Score | Trend | Improvement Initiatives |
|----------------|----------------|--------|-----------------------|
| **Problem Framing** | [Score] | ↗️/→️/↘️ | [Initiatives] |
| **Alternative Generation** | [Score] | ↗️/→️/↘️ | [Initiatives] |
| **Information Gathering** | [Score] | ↗️/→️/↘️ | [Initiatives] |
| **Analysis Quality** | [Score] | ↗️/→️/↘️ | [Initiatives] |

---

## 📋 Action Items & Next Steps

### Decision Process Improvements
- [ ] **[Improvement 1]**: [Description] - [Owner] - [Timeline]
- [ ] **[Improvement 2]**: [Description] - [Owner] - [Timeline]

### Framework Updates
- [ ] **[Framework Update 1]**: [Description] - [Owner] - [Timeline]
- [ ] **[Framework Update 2]**: [Description] - [Owner] - [Timeline]

### Training & Development
- [ ] **[Training 1]**: [Description] - [Audience] - [Timeline]
- [ ] **[Training 2]**: [Description] - [Audience] - [Timeline]

---

## 🔗 Resources & References

### Decision-Making Tools
- **[Tool 1]**: [Description] - [Link]
- **[Tool 2]**: [Description] - [Link]
- **[Tool 3]**: [Description] - [Link]

### Reading & References
- **[Book 1]**: [Author] - [Key takeaways]
- **[Book 2]**: [Author] - [Key takeaways]
- **[Article 1]**: [Publication] - [Key insights]

### External Decision Frameworks
- **[Framework 1]**: [Source] - [When to use]
- **[Framework 2]**: [Source] - [When to use]

---

*Good decisions come from good processes, not from good luck. Consistent application of decision frameworks improves quality and builds organizational trust.*