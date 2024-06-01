
# WRROC <> GA4GH API Conversion Tool Project

## Introduction
The purpose of this document is to explore the mapping between the WRROC (Workflow Run RO-Crate) profiles and the GA4GH Cloud API schemas, focusing specifically on the Task Execution Service (TES) and Workflow Execution Service (WES) APIs. This document aims to address the following questions:

1. How could an RO-Crate be packaged from a TES run, such that the RO-Crate contains all necessary info to restart that TES run?
2. Which additional information is required to package a valid Process Run Crate from the TES run?
3. How could an RO-Crate be packaged from a WES run, such that the RO-Crate contains all necessary info to restart that WES run?
4. Which additional information is required to package a valid Workflow Run Crate from the WES run?

## Mapping of TES to RO-Crate

### Required Information for TES Run
The following table maps the properties of the TES schema to the RO-Crate schema. This mapping ensures that all necessary information from a TES run is captured in the RO-Crate to enable the restart of the TES run.

| TES Property  | RO-Crate Property | Mapping Status | Notes |
|---------------|--------------------|----------------|-------|
| id            | identifier         | 1-to-1 match   |       |
| name          | name               | 1-to-1 match   |       |
| description   | description        | 1-to-1 match   |       |
| state         | status             | Vague match    | Requires additional context |
| inputs        | input              | 1-to-many match| Needs further breakdown |
| outputs       | output             | 1-to-many match| Needs further breakdown |
| resources     | resources          | 1-to-1 match   |       |
| creation_time | dateCreated        | 1-to-1 match   |       |
| start_time    | startTime          | 1-to-1 match   |       |
| end_time      | endTime            | 1-to-1 match   |       |
| ...           | ...                | ...            | ...   |

### Additional Information for Process Run Crate
To create a valid Process Run Crate from a TES run, the following additional properties are required:

| Additional Property       | Required for Process Run Crate | Notes |
|---------------------------|---------------------------------|-------|
| software                  | Yes                             | Details of the software used |
| environment variables     | Yes                             | Environment setup details   |
| provenance                | Yes                             | Provenance information     |
| ...                       | ...                             | ...   |

## Mapping of WES to RO-Crate

### Required Information for WES Run
The following table maps the properties of the WES schema to the RO-Crate schema. This mapping ensures that all necessary information from a WES run is captured in the RO-Crate to enable the restart of the WES run.

| WES Property  | RO-Crate Property | Mapping Status | Notes |
|---------------|--------------------|----------------|-------|
| id            | identifier         | 1-to-1 match   |       |
| workflow_name | name               | 1-to-1 match   |       |
| workflow_params | parameters       | 1-to-1 match   |       |
| workflow_engine_name | engine      | 1-to-1 match   |       |
| state         | status             | Vague match    | Requires additional context |
| inputs        | input              | 1-to-many match| Needs further breakdown |
| outputs       | output             | 1-to-many match| Needs further breakdown |
| creation_time | dateCreated        | 1-to-1 match   |       |
| start_time    | startTime          | 1-to-1 match   |       |
| end_time      | endTime            | 1-to-1 match   |       |
| ...           | ...                | ...            | ...   |

### Additional Information for Workflow Run Crate
To create a valid Workflow Run Crate from a WES run, the following additional properties are required:

| Additional Property       | Required for Workflow Run Crate | Notes |
|---------------------------|----------------------------------|-------|
| software                  | Yes                              | Details of the software used |
| environment variables     | Yes                              | Environment setup details   |
| provenance                | Yes                              | Provenance information     |
| ...                       | ...                              | ...   |

## Summary of Gaps and Recommendations
This section summarizes the gaps identified in the mappings and provides recommendations for addressing these gaps to improve the general applicability of the conversion tool.

- **TES to RO-Crate Gaps:**
  - Detailed breakdown of inputs and outputs required.
  - Clarification on the status property.

- **WES to RO-Crate Gaps:**
  - Detailed breakdown of inputs and outputs required.
  - Clarification on the status property.

### Recommendations
- Propose additions to the RO-Crate profiles to cover missing properties.
- Suggest enhancements to the GA4GH Cloud API schemas to facilitate easier mapping.

## Appendices
- **Appendix A:** Detailed schema definitions for TES, WES, Process Run Crate, and Workflow Run Crate.

---
