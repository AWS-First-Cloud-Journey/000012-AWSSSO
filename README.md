<<<<<<< HEAD
# AWS IAM Identity Center Workshop

A comprehensive hands-on workshop for implementing AWS IAM Identity Center (formerly AWS Single Sign-On) to manage organizational identities across multiple AWS accounts.

## 🎯 Overview

This workshop teaches you how to set up and configure AWS IAM Identity Center for robust identity management in a multi-account AWS environment. You'll learn to implement centralized access controls following the principle of least privilege and Zero Trust security principles.

**Target Audience:** Cloud and IT Administrators  
**Level:** Intermediate  
**Duration:** 1-3 hours  
**Cost:** Free tier eligible (minimal costs for CloudTrail logs)

## 🏗️ Architecture

The workshop guides you through creating a well-architected AWS Landing Zone with:

- **AWS Organization** with 4 Organizational Units (OUs):
  - Security OU
  - Shared Services OU  
  - Logging OU
  - Application OU
- **Centralized Identity Management** via IAM Identity Center
- **Cross-account Access** using IAM roles and permission sets
- **Time-based Access Controls** for enhanced security

## 📚 Workshop Content

### 1. Prerequisites & Setup
- Create AWS accounts within AWS Organizations
- Configure Organizational Units (OUs)
- Invite existing AWS accounts to the organization
- Set up cross-account access roles

### 2. AWS CLI Access
- Manual credential refresh methods
- Automatic credential refresh (recommended)
- SSO configuration for seamless authentication

### 3. Time-based Access Control
- Implement session duration limits
- Configure conditional access policies
- Set up MFA requirements

### 4. Customer Managed Policies
- Create custom permission policies
- Implement fine-grained access controls
- Policy testing and validation

### 5. IAM Identity Center APIs
- Programmatic identity management
- Automated user provisioning
- Integration with external identity providers

### 6. Cleanup
- Resource cleanup procedures
- Cost optimization steps

## 🚀 Getting Started

### Prerequisites

- AWS account not yet part of AWS Organizations
- IAM user with administrative permissions
- Basic understanding of AWS IAM concepts

⚠️ **Important:** Launch an EC2 instance in your account a few hours before starting to ensure account activation.

### Local Development Setup

This workshop uses Hugo static site generator for documentation.

#### Install Hugo

**macOS:**
```bash
brew install hugo
```

**Ubuntu/Debian:**
```bash
sudo apt-get install hugo
```

**Windows:**
```bash
choco install hugo
```

#### Clone and Run

```bash
# Clone the repository
git clone <repository-url>
cd 000012-AWSSSO

# Install theme dependencies
git submodule update --init --recursive

# Start local development server
hugo server -D

# Build for production
hugo
```

The site will be available at `http://localhost:1313`

## 🌐 Multi-language Support

The workshop is available in:
- **English** (Primary)
- **Vietnamese** (Tiếng Việt)

Language switching is available through the site navigation.

## 📁 Project Structure

```
000012-AWSSSO/
├── content/                    # Workshop content
│   ├── 1-prerequisite/        # Setup and prerequisites
│   ├── 2-AWS CLI Access/      # CLI configuration
│   ├── 3-Using Time-based access control/
│   ├── 4-Using Customer Managed Policies/
│   ├── 5-IAM Identity Center Identity Store APIs/
│   └── 6-clean-up/           # Cleanup procedures
├── static/                    # Static assets
│   ├── images/               # Workshop screenshots and diagrams
│   └── css/                  # Custom styling
├── themes/                   # Hugo theme
├── layouts/                  # Custom layout overrides
├── config.toml              # Hugo configuration
└── public/                  # Generated site (after build)
```

## 🔧 Configuration

### Hugo Configuration

Key settings in `config.toml`:
- **Theme:** hugo-theme-learn (workshop-optimized)
- **Multi-language:** English and Vietnamese support
- **Search:** Enabled with JSON index
- **Navigation:** Breadcrumbs and next/prev links

### Theme Customization

- Custom footer with AWS Study Group links
- Workshop-specific color scheme
- Responsive design for mobile devices
- Code syntax highlighting

## 🛡️ Security Considerations

This workshop emphasizes security best practices:

- **Zero Trust Architecture:** Implement least privilege access
- **Multi-Factor Authentication:** Required for sensitive operations
- **Session Management:** Time-based access controls
- **Audit Logging:** Comprehensive activity tracking
- **Cross-Account Security:** Secure role assumption patterns

## 💰 Cost Management

- Most services used are free tier eligible
- Minimal costs for CloudTrail log storage
- EC2 instances for testing (covered by free tier)
- Follow cleanup procedures to avoid ongoing charges

## 🌍 Supported Regions

**Recommended Region:** `us-east-1`

IAM Identity Center is available in most AWS regions. Check the [AWS Regional Services List](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) for current availability.

## 🤝 Contributing

This workshop is part of the AWS First Cloud Journey educational series. To contribute:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally with Hugo
5. Submit a pull request

### Content Guidelines

- Follow the existing markdown structure
- Include step-by-step screenshots
- Test all procedures in a clean AWS account
- Update both English and Vietnamese versions
- Maintain security best practices

## 📞 Support & Community

- **AWS Study Group Blog:** [AWS Blogs](https://aws.amazon.com/blogs)
- **Facebook Community:** [AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj)
- **Email:** journeyoftheaverageguy@gmail.com

## 📄 License

This workshop is provided under the MIT License. See LICENSE file for details.

## 🏷️ Tags

`aws` `iam-identity-center` `sso` `organizations` `security` `workshop` `hugo` `multi-account` `zero-trust`

---

**⚠️ Disclaimer:** This workshop is for educational purposes. Always follow your organization's security policies and AWS best practices when implementing in production environments.
