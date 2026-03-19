# Lab 2 — Thymeleaf Post Method
**Course:** CPAN 228 — Web Application Development
**Student:** Harry Joseph

---

## Overview

This lab builds a fighter registration system using Spring Boot and Thymeleaf. Users fill out a form to register a fighter, which gets validated on the server and then added to an in-memory list. The roster of registered fighters is displayed in a separate table view.

---

## Registration Form

The form collects four fields: name, health, damage, and resistance. Each field has a hint showing the accepted range.

![Fighter registration form](images/01_create_fighter_form.png)

---

## Validation

When invalid data is submitted, the server returns the form with error messages displayed under each failing field. The fighter is not added to the pool until all fields pass validation.

![Form showing validation error messages](images/02_validation_errors.png)

---

## Fighter Added to Roster

After submitting valid data, the server redirects to the fighters page where the new entry appears in the table.

![Fighters roster showing one registered fighter](images/03_fighters_roster.png)

---

## Multiple Fighters Registered

Additional fighters can be registered and all entries accumulate in the same table.

![Fighters roster showing two registered fighters](images/04_two_fighters.png)

---

## Validation Rules

| Field      | Rule                            |
|------------|---------------------------------|
| Name       | Cannot be empty                 |
| Health     | Must be between 1001 and 1499   |
| Damage     | Must be less than 100           |
| Resistance | Must be a decimal from 0 to 10  |

---

## Files Changed

| File | Description |
|---|---|
| `pom.xml` | Fixed invalid dependency IDs and corrected `spring-boot-starter-web` artifact name |
| `Model/Fighter.java` | Added Bean Validation annotations (`@Min`, `@Max`, `@DecimalMin`, `@DecimalMax`, `@NotBlank`, `@NotNull`) |
| `Service/FighterService.java` | New — in-memory fighter pool with `addFighter()` and `getAllFighters()` |
| `controllers/CreateFighterController.java` | New — handles GET to show the form and POST to validate and add a fighter |
| `controllers/FightersController.java` | New — handles GET `/fighters` and renders the roster table |
| `templates/CreateFighter.html` | New — registration form with Bootstrap styling and inline field-level error messages |
| `templates/Fighters.html` | New — roster table using `th:each` to iterate over the fighter list |
| `templates/fragments/navbar.html` | Added Fighters and Create Fighter navigation links |
| `README.md` | Lab completion documentation with screenshots |
| `images/` | Four screenshots showing the form, validation errors, and roster views |

