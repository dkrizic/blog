## Overview

```mermaid
graph LR
    style MOD fill:lightgreen
    style CO fill:lightgreen
    style ORC fill:lightgreen
    style AUT fill:lightgreen
    style IAC fill:yellow
    style TEST fill:lightgreen
    style PAT fill:lightgreen
    style GOVTOOLS fill:lightgreen
    style CLO fill:lightgreen
    style MR fill:yellow
    style LZ fill:yellow
    style AI fill:lightgreen
    subgraph REQ[Requirements]
      A[Availability]
      P[Performance]
      S[Scalability]
      EO[Easy Onboarding]
      I[Insights]
      TTM[Time to Market]
      REP[Reproducibility]
      Q[Quality]
      BC[Best Cost]
      SEC[Security]
      PORT[Portability]
      M[Maintainability]
      GOV[Governance]
      RE[Resilience]
      SUS[Sustainability]
    end
    
    subgraph CNT[Current]
      MS[Microservices]
      subgraph MOD[Modern Languages]
          CL[Compiled]
          MP[Ownership enforcement/Borrow checker]
          AOT[Ahead of Time Compilation]
      end
      subgraph AUT[Automation]
          CICD[Pipeline]
          subgraph IAC[Infrastructure as Code]
            DSO[DevSecOps]
          end
          DEP[Dependency Audit]
          FIN[FinOps]
      end
      subgraph CO[Containers]
        MUL[Multistage build]
      end
      subgraph ORC[Orchestration]
        K8s[Kubernetes]
        AS[Auto Scaling]
      end
      subgraph PAT[Patterns]
          APIF[API First]
          DFR[Design for replace not reuse]
      end
      subgraph AI[AI]
        IDE[IDE Assistance]
        CR[Code Reviews]
        PR[Pull Request Reviews]
      end
      OBS[Observability]
      subgraph CLO[Cloud]
        subgraph MR[Multi-Region]
          MZ[Multi-Zone]
        end
        subgraph LZ[Landing Zones]
          SP[Self Provisioning]
        end
      end
      subgraph GOVTOOLS[Governance Tools]
          PAC[Policy as Code]
          AUD[Audit]
      end
      subgraph TEST[Testing]
        CAN[Canary Releases]
        CON[Contract Testing]
      end
    end
    
    subgraph FUT[Future]
      PF[Platform Engineering]
      subgraph FAI[Future AI]
        AIA[AI Agents]
      end
      AIONBS[AI on Observability data]
      OBSAI[Observability in AI]
    end
    
    A -->|Autoscaling| ORC
    A -->|Scalable|MS
    A --> IAC
    A --> OBS
    A --> MR
    A --> MZ

    S --> MS
    S --> ORC
    S --> CICD
    S --> DEP
    S --> DSO
    
    EO -->|Clear process| CICD
    EO --> SP
    EO --> APIF
    EO --> AI
    EO --> MUL 
    EO --> MS

    P --> MS
    P --> K8s
    P --> AOT
    
    BC --> MS
    BC -->|Autoscaling| ORC
    BC --> CL
    BC --> FIN
    
    TTM -->|Automation| CICD
    TTM -->|Small scope|MS
    TTM --> AI
    TTM -->|Team has full control| SP
    TTM -->|Contract| APIF

    M --> DEP
    M --> APIF
    M --> DFR
    M --> OBS
    M --> CICD
    M --> AI
    M --> IAC
    M --> MS

    I --> OBS
    I --> AI
    
    REP --> CICD
    REP --> CO
    
    Q --> OBS
    Q --> CICD
    Q --> AI
    Q --> APIF
    Q --> MP
    Q --> TEST
    
    SEC --> DEP
    SEC --> IAC
    
    PORT -->|OCI| CO
    PORT -->|Vendor neutral| K8s
    
    AI --> FAI
    OBS --> AIONBS
    FAI --> AIONBS
    OBS --> OBSAI
    
    GOV --> PAC
    GOV --> AUD
    
    SUS --> MS
    SUS --> AS
    SUS --> AUD

    MS --> PF
    MOD --> PF
    AUT --> PF
    TEST --> PF
    PAT --> PF
    GOVTOOLS --> PF
    CLO --> PF
    OBS --> PF
```

## Microservices

```mermaid
graph LR
    subgraph REQ[Requirements]
        A[Availability]
        P[Performance]
        S[Scalability]
        EO[Easy Onboarding]
        TTM[Time to Market]
        BC[Best Cost]
        M[Maintainability]
        SUS[Sustainability]
    end

    subgraph CNT[Current]
        MS[Microservices]
    end

    subgraph FUT[Future]
        PF[Platform Engineering]
    end

    A -->|Scalable|MS

    S --> MS

    EO --> MS

    P --> MS

    BC --> MS

    TTM -->|Small scope|MS

    M --> MS

    SUS --> MS

    MS --> PF
```

## Modern Languages

```mermaid
graph LR
    style MOD fill:lightgreen
    subgraph REQ[Requirements]
        P[Performance]
        BC[Best Cost]
        TTM[Time to Market]
        Q[Quality]
    end
    subgraph CURRENT[Current]
        subgraph MOD[Modern Languages]
            CL[Compiled]
            MP[Ownership enforcement/Borrow checker]
            AOT[Ahead of Time Compilation]
        end
    end
    subgraph FUT[Future]
        PF[Platform Engineering]
    end
    P --> MOD
    BC --> CL
    TTM --> AOT
    Q --> MP
    MOD --> PF
```

## Containers

```mermaid
graph LR
    style CO fill:lightgreen
    subgraph REQ[Requirements]
        REP[Reproducibility]
        EO[Easy Onboarding]
        BC[Best Cost]
    end
    subgraph CURRENT[Current]
        subgraph CO[Containers]
            MUL[Multistage build]
        end
    end
    subgraph FUT[Future]
        PF[Platform Engineering]
    end
    REP --> CO
    EO --> MUL
    BC --> CO
    CO --> PF
```

## Orchestration

```mermaid
graph LR
    style ORC fill:lightgreen
    subgraph REQ[Requirements]
        A[Availability]
        S[Scalability]
        P[Performance]
    end
    subgraph CNT[Current]
        subgraph ORC[Orchestration]
            K8s[Kubernetes]
            AS[Auto Scaling]
        end
    end
    subgraph FUT[Future]
        PF[Platform Engineering]
    end
    A -->|Autoscaling| ORC
    S --> ORC
    P --> K8s
    ORC --> PF
```

## Automation

```mermaid
graph LR
    style AUT fill:lightgreen
    style IAC fill:yellow
    subgraph REQ[Requirements]
        S[Scalability]
        EO[Easy Onboarding]
        TTM[Time to Market]
        M[Maintainability]
        SEC[Security]
    end
    subgraph CNT[Current]
        subgraph AUT[Automation]
            CICD[Pipeline]
            subgraph IAC[Infrastructure as Code]
                DSO[DevSecOps]
            end
            DEP[Dependency Audit]
            FIN[FinOps]
        end
    end
    subgraph FUT[Future]
        PF[Platform Engineering]
    end
    S --> CICD
    S --> DEP
    S --> DSO  
    EO -->|Clear process| CICD
    TTM -->|Automation| CICD
    M --> DEP
    M --> CICD
    SEC --> DEP
    SEC --> IAC
    IAC --> PF
    CICD --> PF
```
## Patterns

```mermaid
graph LR
    style PAT fill:lightgreen
    subgraph REQ[Requirements]
        EO[Easy Onboarding]
        TTM[Time to Market]
        M[Maintainability]
    end
    subgraph CNT[Current]
        subgraph PAT[Patterns]
            APIF[API First]
            DFR[Design for replace not reuse]
        end
    end
    subgraph FUT[Future]
        PF[Platform Engineering]
    end
    EO --> APIF
    EO --> DFR
    TTM -->|Contract| APIF
    M --> APIF
    M --> DFR
    PAT --> PF
```

## AI

```mermaid
graph LR
    style AI fill:lightgreen
    subgraph REQ[Requirements]
        EO[Easy Onboarding]
        TTM[Time to Market]
        M[Maintainability]
        I[Insights]
        Q[Quality]
    end
    subgraph CNT[Current]
        subgraph AI[AI]
            IDE[IDE Assistance]
            CR[Code Reviews]
            PR[Pull Request Reviews]
        end
    end
    subgraph FUT[Future]
        PF[Platform Engineering]
        subgraph FAI[Future AI]
            AIA[AI Agents]
        end
        AIONBS[AI on Observability data]
        OBSAI[Observability in AI]
    end
    EO --> AI
    TTM --> AI
    M --> AI
    I --> AI
    Q --> AI
    AI --> FAI
    FAI --> AIONBS
    AI --> PF
```

## Observability

```mermaid
graph LR
    subgraph REQ[Requirements]
        A[Availability]
        EO[Easy Onboarding]
        M[Maintainability]
        I[Insights]
        REP[Reproducibility]
        Q[Quality]
    end
    subgraph CNT[Current]
        OBS[Observability]
    end
    subgraph FUT[Future]
        PF[Platform Engineering]
        AIONBS[AI on Observability data]
        OBSAI[Observability in AI]
    end
    A --> OBS
    EO --> OBS
    M --> OBS
    I --> OBS
    REP --> OBS
    Q --> OBS
    OBS --> AIONBS
    OBS --> OBSAI
    OBS --> PF
```

## Cloud

```mermaid
graph LR
    style CLO fill:lightgreen
    style MR fill:yellow
    style LZ fill:yellow
    subgraph REQ[Requirements]
        A[Availability]
        EO[Easy Onboarding]
        TTM[Time to Market]
    end
    subgraph CNT[Current]
        subgraph CLO[Cloud]
            subgraph MR[Multi-Region]
                MZ[Multi-Zone]
            end
            subgraph LZ[Landing Zones]
                SP[Self Provisioning]
            end
        end
    end
    subgraph FUT[Future]
        PF[Platform Engineering]
    end
    A --> MR
    A --> MZ
    EO --> SP
    CLO --> PF
    TTM -->|Team has full control| SP
```

## Governance Tools

```mermaid
graph LR
    style GOVTOOLS fill:lightgreen
    subgraph REQ[Requirements]
        GOV[Governance]
        SUS[Sustainability]
    end
    subgraph CNT[Current]
        subgraph GOVTOOLS[Governance Tools]
            PAC[Policy as Code]
            AUD[Audit]
        end
    end
    subgraph FUT[Future]
        PF[Platform Engineering]
    end
    GOV --> PAC
    GOV --> AUD
    SUS --> AUD
    GOVTOOLS --> PF
```

## Testing

```mermaid
graph LR
    style TEST fill:lightgreen
    subgraph REQ[Requirements]
        Q[Quality]
    end
    subgraph CNT[Current]
        subgraph TEST[Testing]
            CAN[Canary Releases]
            CON[Contract Testing]
        end
    end
    subgraph FUT[Future]
        PF[Platform Engineering]
    end
    Q --> TEST
    TEST --> PF
```

