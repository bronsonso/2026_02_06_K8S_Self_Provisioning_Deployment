```
yaml

# ==============================================
# Kubernetes Resource Request Form
# For WordPress/Web Application Deployment
# ==============================================
# Save this file and send to: support@hkecl.net
# ==============================================

apiVersion: hkecl.net/v1alpha1
kind: ResourceRequest
metadata:
  requestId: "auto-generated-on-submit"  # Will be filled by system
  createdAt: "2024-11-15T10:30:00Z"      # Auto-filled
  department: "Marketing"                # Your department

# ====================G
# SECTION 1: REQUESTER
# ====================
requester:
  name: "John Smith"
  email: "john.smith@hkecl.net"
  employeeId: "HKECL-2024-001"
  phoneExtension: "x1234"
  manager:
    name: "Jane Doe"
    email: "jane.doe@hkecl.net"

# =====================
# SECTION 2: PROJECT
# =====================
project:
  name: "wordpress-marketing-blog"
  code: "MKT-BLOG-2024"                 # Cost center code
  description: |
    Public-facing WordPress site for marketing team blog,
    news announcements, and customer resources.
    
  justification: |
    Required for Q4 marketing campaign to increase
    brand visibility and customer engagement.
    
  type: "wordpress"                     # wordpress | custom | api | database
  priority: "medium"                    # low | medium | high | critical
  launchDate: "2024-12-01"              # YYYY-MM-DD
  duration: "permanent"                 # temporary | permanent
  endDate: ""                           # YYYY-MM-DD (if temporary)
  
  # For WordPress specific
  wordpress:
    version: "latest"                   # latest | 6.4 | 6.3
    multisite: false
    migration:
      required: false
      backupLocation: ""                # URL or path to existing backup
    plugins:
      required:
        - "yoast-seo"
        - "wordfence-security"
        - "w3-total-cache"
        - "contact-form-7"
      custom:                           # Custom/paid plugins
        - name: "advanced-custom-fields-pro"
          license: "company-license-key-123"
    
    theme:
      type: "custom"                    # default | custom | premium
      repository: "https://github.com/hkecl/marketing-theme"
      branch: "main"

# ==========================
# SECTION 3: RESOURCE TIER
# ==========================
resources:
  # Choose ONE tier or use custom
  tier: "standard"                      # development | standard | premium | custom
  
  # If tier=custom, fill below:
  custom:
    cpu: 2                             # CPU cores per pod
    memory: "4Gi"                       # Memory per pod
    storage: "50Gi"                     # Storage per volume

  scaling:
    minReplicas: 2                      # Minimum number of pods
    maxReplicas: 5                      # Maximum number of pods
    autoscale:
      enabled: true
      metric: "cpu"                     # cpu | memory | custom
      target: 70                        # Percentage threshold
      cooldown: 300                     # Seconds between scaling events

# ==========================
# SECTION 4: STORAGE
# ==========================
storage:
  # WordPress files storage
  wordpress:
    size: "50Gi"
    accessMode: "ReadWriteMany"         # ReadWriteOnce | ReadWriteMany
    storageClass: "ssd"                 # ssd | hdd | premium
    
  # Database storage
  database:
    type: "mysql"                       # mysql | mariadb
    version: "8.0"
    size: "50Gi"
    performance: "high"                 # standard | high | premium
    replication:
      enabled: true
      replicas: 1                       # Number of read replicas
      
  # Backup storage
  backup:
    size: "100Gi"
    retention:
      daily: 30                         # Keep daily backups for X days
      weekly: 12                        # Keep weekly backups for X weeks
      monthly: 12                       # Keep monthly backups for X months
    schedule:
      full: "daily"                     # daily | weekly
      incremental: "6h"                 # 6h | 12h | 24h
      window: "00:00-04:00"             # Backup window UTC

# ==========================
# SECTION 5: NETWORKING
# ==========================
networking:
  domains:
    primary: "blog.hkecl.net"
    aliases:
      - "www.blog.hkecl.net"
      - "marketing.hkecl.net"
      
  ssl:
    provider: "lets-encrypt"            # lets-encrypt | custom | purchase
    autoRenew: true
    customCertificate:                   # If using custom cert
      secretName: ""
      namespace: ""
      
  access:
    type: "public"                      # public | internal | vpn-only
    ipRestrictions:                     # Optional IP restrictions
      admin: []
      public: []
      
  cdn:
    enabled: true
    provider: "cloudflare"              # cloudflare | aws-cloudfront | none
    waf: true                           # Web Application Firewall

# ==========================
# SECTION 6: DATABASE
# ==========================
database:
  # Only needed if not using default WordPress database
  external:
    required: false
    type: ""                           # rds | cloud-sql | external-hosted
    connectionString: ""
    credentials:
      secretName: ""
      key: ""

# ==========================
# SECTION 7: DISASTER RECOVERY
# ==========================
disasterRecovery:
  rto: "4h"                            # Recovery Time Objective
  rpo: "1h"                            # Recovery Point Objective
  
  backupTesting:
    frequency: "monthly"               # monthly | quarterly | never
    lastTested: ""                     # YYYY-MM-DD
  
  # Disaster recovery sites
  drSites:
    - name: "aws-eu-west-1"
      enabled: false
      type: "warm-standby"            # cold-standby | warm-standby | hot-standby

# ==========================
# SECTION 8: MONITORING
# ==========================
monitoring:
  uptime:
    enabled: true
    checkInterval: "60s"               # 30s | 60s | 5m
    
  metrics:
    level: "advanced"                  # basic | advanced | custom
    retention: "30d"                   # 7d | 30d | 90d
    
  logging:
    enabled: true
    retention: "30d"
    exportTo: ["splunk", "elk"]        # splunk | elk | datadog | none
    
  alerting:
    channels:
      email:
        - "john.smith@hkecl.net"
        - "team-marketing@hkecl.net"
      slack: "#marketing-alerts"
      teams: "Marketing Team Channel"
      
    thresholds:
      cpu: 80                          # Percent
      memory: 85                       # Percent
      disk: 90                         # Percent
      responseTime: "2s"               # Seconds

# ==========================
# SECTION 9: TEAM ACCESS
# ==========================
team:
  members:
    - name: "John Smith"
      email: "john.smith@hkecl.net"
      role: "owner"                    # owner | admin | developer | editor
      k8sAccess: true                  # Kubernetes dashboard access
      
    - name: "Sarah Chen"
      email: "sarah.chen@hkecl.net"
      role: "editor"
      k8sAccess: false
      
    - name: "Mike Johnson"
      email: "mike.johnson@hkecl.net"
      role: "developer"
      k8sAccess: true

  # External collaborators (if any)
  external:
    - company: "Design Agency Inc"
      contact: "design@agency.com"
      access: "ftp-only"               # ftp-only | sftp | limited-admin
      expiration: "2025-01-31"

# ==========================
# SECTION 10: COMPLIANCE
# ==========================
compliance:
  gdpr: true
  accessibility: true                  # WCAG 2.1 compliance
  dataResidency: "hong-kong"          # hong-kong | eu | us | global
  
  security:
    pentestRequired: false
    scheduled: ""                      # YYYY-MM-DD
    scanner:
      enabled: true
      frequency: "daily"               # daily | weekly | monthly
    
  audits:
    logsRetention: "7y"                # Years
    accessLogging: true

# ==========================
# SECTION 11: BUDGET
# ==========================
budget:
  costCenter: "MKT-2024-Q4"
  poNumber: "PO-2024-MKT-045"
  monthlyLimit: 500                    # USD per month
  approval:
    manager: "jane.doe@hkecl.net"
    finance: "finance@hkecl.net"
    approved: false                    # Will be set by approvers
    
  # Estimated costs (auto-calculated)
  estimates:
    infrastructure: 120                # Monthly USD
    storage: 50
    network: 30
    monitoring: 20
    total: 220

# ==========================
# SECTION 12: TIMELINE
# ==========================
timeline:
  phases:
    - name: "Provisioning"
      start: "2024-11-20"
      end: "2024-11-22"
      dependencies: []
      
    - name: "Development"
      start: "2024-11-23"
      end: "2024-11-30"
      dependencies: ["Provisioning"]
      
    - name: "Testing"
      start: "2024-12-01"
      end: "2024-12-05"
      dependencies: ["Development"]
      
    - name: "Go-Live"
      start: "2024-12-06"
      dependencies: ["Testing"]

# ==========================
# SECTION 13: ENVIRONMENTS
# ==========================
environments:
  - name: "development"
    enabled: true
    resources:
      tier: "development"
      replicas: 1
    access: "internal-only"
    
  - name: "staging"
    enabled: true
    resources:
      tier: "standard"
      replicas: 2
    access: "vpn-only"
    
  - name: "production"
    enabled: true
    resources:
      tier: "standard"
      replicas: 3
    access: "public"

# ==========================
# SECTION 14: ADDITIONAL SERVICES
# ==========================
services:
  # Caching
  redis:
    enabled: true
    size: "1Gi"
    version: "7.0"
    
  # Search
  elasticsearch:
    enabled: false
    size: ""
    version: ""
    
  # Email
  email:
    provider: "smtp-relay"            # smtp-relay | sendgrid | mailgun | ses
    dailyLimit: 1000                  # Emails per day
    attachments: true
    
  # CDN
  cdn:
    provider: "cloudflare"
    plan: "enterprise"
    
  # Image optimization
  imageOptimization:
    enabled: true
    provider: "imagify"               # imagify | shortpixel | kraken

# ==========================
# SECTION 15: MIGRATION (If applicable)
# ==========================
migration:
  required: false
  source:
    type: ""                          # shared-hosting | vps | other-k8s
    url: ""
    credentials:
      secretName: ""
  data:
    - type: "database"
      size: "2GB"
    - type: "uploads"
      size: "15GB"
    - type: "themes-plugins"
      size: "500MB"
      
  schedule:
    window: "2024-11-20T02:00:00Z"
    downtime: "1h"                    # Expected downtime

# ==========================
# SECTION 16: ATTACHMENTS
# ==========================
attachments:
  # List files attached with this request
  files:
    - name: "architecture-diagram.png"
      purpose: "System design"
      
    - name: "content-migration-plan.docx"
      purpose: "Migration strategy"
      
    - name: "budget-approval.pdf"
      purpose: "Finance approval"

# ==========================
# VALIDATION & SUBMISSION
# ==========================
validation:
  checklist:
    - "Budget approved by finance"
    - "Domain names registered"
    - "Content ready for migration"
    - "Team members notified"
    - "Security review completed"
    
  terms:
    accepted: false                    # Must be true to submit
    acceptedBy: ""
    acceptedAt: ""

# ==============================================
# INSTRUCTIONS:
# 1. Fill in all required fields (marked with *)
# 2. Replace placeholder values with your data
# 3. Remove sections that don't apply
# 4. Save as: [project-name]-request.yaml
# 5. Email to: support@hkecl.net
# ==============================================
```