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

* Microservices architecture breaks down applications into smaller, independent services that can be developed, deployed, and scaled individually.
* This approach enhances availability and scalability, as services can be scaled based on demand.
* The smaller scope of microservices allows for faster development cycles, improving time to market.
* Microservices also promote maintainability by isolating changes to specific services, reducing the risk of impacting the entire application.
* Sustainability is improved through efficient resource usage, as services can be scaled independently based on their specific needs.
* Microservices can lead to cost savings by optimizing resource allocation and reducing over-provisioning.

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

* Modern programming languages that are compiled (e.g., Rust, Go) offer performance benefits and lower runtime costs compared to interpreted languages.
* Ownership enforcement and borrow checking (as seen in Rust) help catch memory safety issues at compile time, improving code quality and reducing runtime errors.
* Ahead-of-Time (AOT) compilation can reduce startup times and improve performance, which is particularly beneficial for serverless and microservices architectures.
* Modern languages often come with robust ecosystems and tooling that can accelerate development and time to market.

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

* Containers package applications and their dependencies into a standardized unit for software development, ensuring consistency across different environments.
* Multistage builds optimize container images by reducing their size and improving build efficiency, leading to cost savings in storage and bandwidth.
* Multistage builds also simplify the onboarding process by providing a clear and efficient way to build and deploy applications.

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

* **Orchestration** platforms like Kubernetes manage the deployment, scaling, and operation of containerized applications.
* **Auto Scaling** automatically adjusts the number of running instances based on demand, improving availability and cost efficiency.

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
        BC[Best Cost]
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
    EO --> IAC
    TTM -->|Automation| CICD
    M --> DEP
    M --> CICD
    SEC --> DEP
    SEC --> IAC
    AUT --> PF
    BC --> FIN
```

* Infrastructure is created and managed using code and automation tools to ensure consistency, repeatability, and version control.
* DevSecOps integrates security practices into the DevOps process, ensuring that security is considered at every stage of the software development lifecycle.
* Dependency audits help identify and mitigate vulnerabilities in third-party libraries and packages used in the software.
* FinOps focuses on optimizing cloud costs and resource usage to achieve the best cost efficiency.

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

* API should be defined first (e.g. Protobuf, OpenAPI, GraphQL schema) before implementation to ensure clear contracts between services.
* Design services to be replaceable rather than reusable to facilitate easier updates and technology changes in the future.

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

* AI-powered tools assist developers with code completion, reviews, and pull request analysis, improving productivity and code quality.
* Future AI agents could further automate development tasks, enhancing onboarding, time to market, maintainability, insights, and quality.
* AI can also be leveraged to analyze observability data for deeper insights and improved system performance.
* Observability can be integrated into AI systems to enhance their monitoring and reliability.

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

* Observability provides insights into the health and performance of applications through metrics, logs, and traces.
* It enhances availability by enabling proactive monitoring and alerting for potential issues.
* Observability data aids in maintainability by facilitating debugging and root cause analysis.
* It provides insights into system behavior, helping teams make informed decisions.
* Observability supports reproducibility by capturing the state of the system during incidents.
* It contributes to quality by enabling continuous improvement based on observed performance and user experience.
* Observability data can be leveraged by AI to derive deeper insights and automate responses to incidents.

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

* Cloud providers offer multiple regions and each region contains multiple availability zones (AZs). Deploying applications across multiple AZs within a region enhances availability by mitigating the impact of an AZ failure.
* Multi-region deployments further improve availability by protecting against region-wide outages, ensuring that applications remain accessible even if an entire region goes down.
* Self-provisioning landing zones allow teams to quickly set up their cloud environments without waiting for centralized IT, speeding up onboarding and time to market.
* Having control over their own landing zones enables teams to deploy and manage resources more efficiently, reducing dependencies and delays.
* Cloud infrastructure provides the scalability and flexibility needed to support modern applications, allowing teams to adapt quickly to changing requirements.
* Cloud providers often offer built-in tools and services that can enhance observability, security, and cost management, further supporting the overall platform engineering efforts.
* Cloud-native services can help optimize resource usage, contributing to sustainability goals by reducing waste and improving efficiency.
* Utilizing cloud services can lead to cost savings through pay-as-you-go pricing models and the ability to scale resources based on demand.
* Cloud providers often have robust security measures in place, helping to ensure compliance with industry standards and regulations.
* Cloud platforms typically offer a wide range of services and tools that can accelerate development and deployment processes, improving time to market.
* Cloud environments can be designed to be portable, allowing applications to be moved between different cloud providers or on-premises environments as needed.
* Cloud providers frequently update their services and infrastructure, ensuring that teams have access to the latest technologies and features without the need for manual upgrades.
* Cloud platforms often provide extensive documentation, training resources, and community support, making it easier for teams to learn and adopt new technologies.
* Cloud providers typically offer robust disaster recovery and backup solutions, enhancing the resilience of applications and data.
* Cloud environments can be designed to support compliance with various regulatory requirements, helping organizations meet their legal obligations.
* Cloud providers often have global networks of data centers, enabling low-latency access to applications and services for users around the world.
* Cloud platforms can facilitate collaboration among distributed teams by providing shared access to resources and tools.
* Cloud providers often offer advanced analytics and machine learning services that can enhance application capabilities and provide deeper insights into user behavior and system performance.
* Cloud environments can be designed to support hybrid and multi-cloud strategies, providing flexibility and reducing vendor lock-in.
* Cloud providers frequently invest in sustainability initiatives, such as using renewable energy and optimizing data center efficiency, helping organizations reduce their environmental impact.
* Cloud platforms often provide tools for monitoring and managing costs, enabling teams to optimize their spending and improve financial accountability.
* Cloud providers typically offer robust identity and access management solutions, enhancing the security of applications and data.
* Cloud environments can be designed to support continuous integration and continuous deployment (CI/CD) practices, streamlining development workflows and improving software quality.
* Cloud providers often have extensive partner ecosystems, offering a wide range of third-party tools and services that can enhance application capabilities and support various use cases.


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

* Governance tools help enforce policies and conduct audits to ensure compliance with organizational standards and regulations.
* Sustainability initiatives can be supported through auditing resource usage and promoting efficient practices.

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

* Testing strategies like canary releases and contract testing help ensure software quality by validating changes in controlled environments before full deployment.
* Canary releases allow teams to deploy new features to a small subset of users, monitoring for issues before rolling out to the entire user base.
* Contract testing verifies that services adhere to defined API contracts, reducing integration issues and improving reliability.
* These testing practices contribute to overall software quality by catching issues early and ensuring that services work as expected.
* Implementing robust testing strategies enhances confidence in deployments, leading to more stable and reliable applications.
