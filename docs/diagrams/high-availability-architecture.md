Key high availability components:

- Multi-AZ deployments for all services
- Auto-scaling for EC2 instances
- Database replication (RDS Multi-AZ)
- S3 cross-region replication for disaster recovery
- Load balancing across availability zones
- Automated failover for critical services

```mermaid
flowchart TD
    subgraph "Region A - Primary"
        subgraph "Availability Zone 1"
            A1[EC2 Instance 1] --> B1[ALB - Zone 1]
            C1[RDS Primary] --> D1[Redis Primary]
        end
        
        subgraph "Availability Zone 2"
            A2[EC2 Instance 2] --> B2[ALB - Zone 2]
            C2[RDS Standby] --> D2[Redis Replica]
        end
        
        B1 --> E1[Application Load Balancer]
        B2 --> E1
        F1[S3 Bucket - Primary]
    end
    
    subgraph "Region B - DR"
        subgraph "Availability Zone 1"
            G1[EC2 Instance DR] --> H1[ALB DR - Zone 1]
            I1[RDS DR] --> J1[Redis DR]
        end
        
        H1 --> K1[Application Load Balancer DR]
        L1[S3 Bucket - DR]
    end
    
    F1 -.->|Cross-Region Replication| L1
    C1 -.->|Async Replication| I1
    
    subgraph "Global Resources"
        M[Route 53] --> E1
        M -->|Failover| K1
        N[CloudFront CDN]
    end
    
    subgraph "Recovery Components"
        O[AWS Backup]
        P[Recovery Point Objectives]
        Q[Recovery Time Objectives]
    end
```