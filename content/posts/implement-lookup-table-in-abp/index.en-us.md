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

A lookup table is a master list that maps business keys to values and is referenced by other tables. The ABP Framework follows Domain-Driven Design (DDD) best practices, which do not align well with traditional lookup-table patterns. This article explains how to implement lookup tables for an ABP application by separating lookup-table responsibility from the DDD domain and placing it in the infrastructure layer.

This guide is intended for developers using the ABP Framework who need to represent stable reference data (for example, status codes or country lists) while preserving DDD principles. It covers design choices, implementation patterns, and trade-offs.
