---
date: '2025-10-29T16:39:08+08:00'
draft: true
title: 'Implement Lookup Table in The ABP Framework'
description: ''
author: "Charles Zhang"
authorLink: "https://github.com/realZhangChi"
resources:
- name: "featured-image"
  src: "featured-image.jpg"
---

A lookup table is a master list that defines groups of configurable values. These values are consumed by other entities and can be edited dynamically or extended with new values at runtime. Many systems use lookup tables to manage properties such as `JobTitle` and `Department` for the `Employee` entity. This approach simplifies development and data storage but does not align well with Domain-Driven Design (DDD) principles. This article shows how to implement lookup tables in an ABP application using a shared-type entity, by separating the lookup-table responsibility from the DDD domain and placing it in the infrastructure layer.

## The Problem with Traditional Lookup Tables

Consider an application that defines an `Employee` entity with two properties: `JobTitle` and `Department`. For example:

``` csharp
public class Employee
{
    public string JobTitle { get; set; }

    public string Department { get; set; }
}
```

Those properties accept values that are managed at runtime, administrators can add or remove valid values without recompiling. Therefore, the application stores allowed values in a runtime-managed lookup table. Each lookup row include a `Type` field that groups related values (`Type` = 'JobTitle' or `Type` = 'Department'); the lookup entity looks like this:

``` csharp
public class Lookup
{
    public string Type { get; set; }

    public string Name { get; set; }
}
```
