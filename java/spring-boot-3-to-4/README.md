![Java](https://img.shields.io/badge/Java-17%2B-ED8B00?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.x-6DB33F?logo=springboot&logoColor=white)
![GitHub Copilot](https://img.shields.io/badge/GitHub-Copilot-000000?logo=github&logoColor=white)
![Migration](https://img.shields.io/badge/Migration-Spring%20Boot%203%E2%86%924-blue)
![Stars](https://img.shields.io/github/stars/eddybenchek/copilot-migration-playbooks?style=social)

# Spring Boot 3 → Spring Boot 4 Migration Guide

This playbook documents a **practical, production-safe strategy** to migrate a Spring Boot 3.x application to **Spring Boot 4.x**.

Unlike the Spring Boot 2 → 3 jump (Jakarta), this migration is usually **less about namespaces** and more about:
- **Spring Framework baseline changes**
- Dependency alignment and ecosystem readiness
- Deprecations removed and stricter defaults
- Testing, observability, and runtime verification

This guide uses **GitHub Copilot** to accelerate bulk edits, audit deprecations, and generate validation code.

---

## High-Level Strategy

1. Create a migration branch and freeze risky changes
2. Align Java + build tooling and verify CI
3. Upgrade Spring Boot + dependency BOM
4. Fix compilation issues and removed APIs
5. Verify runtime behavior and configuration
6. Run full regression (tests + staging + smoke checks)
7. Cleanup and stabilize

---

## Copilot Prompts Used

### Project Compatibility Scan

```text
Analyze this Spring Boot 3.x codebase for Spring Boot 4 migration risks.
List breaking changes, deprecated APIs that may be removed, and any dependency compatibility concerns.
Output a prioritized checklist.
Do not modify code.
```

### Deprecations Cleanup


```text
Find deprecated Spring / Spring Boot APIs in this project and propose Spring Boot 4 compatible replacements.
Apply changes incrementally and avoid business logic changes.
```

### Configuration & Runtime Validation

```text
Review application configuration (application.yml/properties) and update for Spring Boot 4 compatibility.
Call out risky defaults or behavior changes.
Suggest a validation checklist and smoke test plan.
```

---

## Common Breaking Areas to Audit

- Removed deprecated Spring APIs (compile-time breaks)
- Auto-configuration behavior changes
- Security configuration and filters
- Actuator endpoints and observability defaults
- Validation + binding strictness
- Third-party starters and plugins compatibility

---

## Minimal Maven Baseline

```xml
<properties>
  <java.version>17</java.version>
</properties>

<dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-dependencies</artifactId>
      <version>4.0.0</version>
      <type>pom</type>
      <scope>import</scope>
    </dependency>
  </dependencies>
</dependencyManagement>
```
Use the exact Spring Boot 4 version you target in production.

---

## Full Step-by-Step Migration Guide

👉 Read the full Spring Boot 3 → 4 migration guide on CopilotHub:
https://copilothub.directory/instructions/spring-boot-3x-to-40-migration-guide

- The full guide includes:
- Detailed checklists
- Compatibility notes
- Copilot workflows for large changes
- Validation and rollback strategies
  
---

## Related Playbooks

-   Java 8 → Java 17 Migration
    
-   Hibernate 5 → Hibernate 6 Upgrade
    
-   Monolith → Modular Spring Boot Architecture
    
---

## Feedback & Contributions

If you’ve migrated a Spring Boot application recently and noticed edge cases or pitfalls not covered here, feel free to open an issue or submit a pull request.

⭐ If this playbook helped you, consider starring the repo.
