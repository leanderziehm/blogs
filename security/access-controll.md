# Access Controll

authentication, authorization, and audit.





#### 1. Role-Based Access Control (RBAC)

Still the most widely deployed model in companies, operating systems, databases, and cloud platforms (AWS, Azure, Kubernetes). It’s simple, scalable, and maps well to job roles.

#### 2. Attribute-Based Access Control (ABAC)

Very common in modern cloud-native and zero-trust architectures. Popular in large-scale systems where context matters (device type, location, time, risk score). It’s increasingly used but more complex than RBAC.

#### 3. Rule-Based Access Control (RAC)

Often used as an extension of RBAC/ABAC (e.g., time-based or condition-based rules). Common in enterprise environments but usually not the primary model.

#### 4. Discretionary Access Control (DAC)

Still found in traditional file systems (like Unix-style permissions), but less dominant in modern enterprise identity systems because it doesn’t scale well for large organizations.

#### 5. Mandatory Access Control (MAC)

Very common in high-security/government/military systems (e.g., classified environments, SELinux). Not widely used in general business applications.

#### 6. Relationship-Based Access Control (ReBAC)

Growing fast in social platforms and graph-based systems (Google Zanzibar-style systems). Still emerging in mainstream enterprise tooling.
