![Last Updated](https://img.shields.io/github/last-commit/eddybenchek/copilot-migration-playbooks)
![Java](https://img.shields.io/badge/Java-17-ED8B00?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-6DB33F?logo=springboot&logoColor=white)
![GitHub Copilot](https://img.shields.io/badge/Powered%20by-GitHub%20Copilot-000000?logo=github)
![Migration](https://img.shields.io/badge/Migration-Spring%20Boot%202→3-blue)
![Stars](https://img.shields.io/github/stars/eddybenchek/copilot-migration-playbooks?style=social)


# Spring Boot 2 → Spring Boot 3 Migration (Jakarta EE)

This playbook documents a **practical, production-safe strategy** to migrate a Spring Boot 2.x application to **Spring Boot 3.x**.

The upgrade is **not a simple version bump** — it introduces:
- Jakarta EE namespace changes (`javax → jakarta`)
- Java 17 minimum requirement
- Spring Framework 6
- Hibernate 6
- Spring Security API changes

This guide focuses on **incremental migration** using **GitHub Copilot** to assist
with bulk refactors and validation.

---

## Table of Contents

- [Why This Migration Matters](#why-this-migration-matters)
- [High-Level Migration Strategy](#high-level-migration-strategy)
- [Copilot Prompts Used](#copilot-prompts-used)
- [Common Breaking Changes](#common-breaking-changes)
- [Minimal Maven Example](#minimal-maven-example)
- [Common Pitfalls](#common-pitfalls)
- [Full Step-by-Step Migration Guide](#full-step-by-step-migration-guide)
- [Related Playbooks](#related-playbooks)
- [Why GitHub Copilot Helps Here](#why-github-copilot-helps-here)
- [Feedback & Contributions](#feedback--contributions)

---

<a id="why-this-migration-matters"></a>
## Why This Migration Matters

Many production systems are still running on Spring Boot 2.x.
Spring Boot 3.x is now the actively supported baseline and unlocks:

- Long-term security updates
- Compatibility with modern Java runtimes
- Cleaner APIs and framework internals
- Improved performance and observability

---

<a id="high-level-migration-strategy"></a>
## High-Level Migration Strategy

The safest approach is **incremental**:

1. Upgrade Java to 17+
2. Align dependencies with Spring Boot 3.x
3. Migrate `javax.*` imports to `jakarta.*`
4. Update Spring Security configuration
5. Validate Hibernate and JPA behavior
6. Run full regression tests before cleanup

---

<a id="copilot-prompts-used"></a>
## Copilot Prompts Used

### Project Analysis Prompt

```text
Analyze this Spring Boot 2.x codebase and identify all incompatibilities with Spring Boot 3.x.
Focus on Jakarta EE namespace changes, Spring Security 6, and Hibernate 6.
Provide a prioritized migration checklist.
```

### Jakarta Namespace Refactor

```text
Refactor all javax.* imports to jakarta.*.
Ensure Spring Boot 3 compatibility.
Do not change business logic.
Highlight files that require manual review.
```

### Security Migration Validation

```text
Review this Spring Security configuration and update it for Spring Boot 3.x and Spring Security 6.
Replace deprecated APIs and explain each breaking change.
```

---

<a id="common-breaking-changes"></a>
## Common Breaking Changes

- `javax.persistence` → `jakarta.persistence`
- `WebSecurityConfigurerAdapter` removal
- Hibernate 6 query behavior differences
- Actuator endpoint path changes
- Deprecated starters removed

---

<a id="minimal-maven-example"></a>
## Minimal Maven Example

> This example shows the **minimum required alignment** for Spring Boot 3.x.
> Your actual `pom.xml` may include additional plugins and dependencies.

```xml
<properties>
  <java.version>17</java.version>
</properties>

<dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-dependencies</artifactId>
      <version>3.2.0</version>
      <type>pom</type>
      <scope>import</scope>
    </dependency>
  </dependencies>
</dependencyManagement>
```

---

<a id="common-pitfalls"></a>
## Common Pitfalls

-   Attempting a “big bang” migration
    
-   Enabling strict validation before code compiles
    
-   Missing transitive `javax` dependencies
    
-   Skipping integration tests
    
---

## Tested Against

- Spring Boot 2.6 → 3.2
- Java 11 → 17
- Spring Security 5 → 6
- Hibernate 5 → 6
- Maven & Gradle builds

---

<a id="full-step-by-step-migration-guide"></a>
## Full Step-by-Step Migration Guide

👉 **Read the complete Spring Boot 2 → 3 migration playbook on CopilotHub:**  
https://copilothub.directory/instructions/spring-boot-2-to-3-migration

The full guide includes:

-   Detailed checklists
    
-   Dependency compatibility tables
    
-   Copilot-powered refactoring workflows
    
-   Validation steps and rollback strategies
    

---

<a id="related-playbooks"></a>
## Related Playbooks

-   Java 8 → Java 17 Migration
    
-   Hibernate 5 → Hibernate 6 Upgrade
    
-   Monolith → Modular Spring Boot Architecture
    
---

<a id="why-github-copilot-helps-here"></a>
## Why GitHub Copilot Helps Here

Spring Boot 3 migrations involve large-scale mechanical changes.  
Copilot is particularly effective for:

-   Namespace refactors
    
-   Updating deprecated APIs
    
-   Suggesting compatible configurations
    
-   Generating validation and test code
    
---

<a id="feedback-and-contributions"></a>
## Feedback & Contributions

If you’ve migrated a Spring Boot application recently and noticed edge cases or pitfalls not covered here, feel free to open an issue or submit a pull request.

⭐ If this playbook helped you, consider starring the repo.
