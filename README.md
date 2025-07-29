📦 Scan Event Correlation – One Part of the Search Result for the Dashboard
This Splunk SPL query is one component of a larger dashboard used for visualizing and analyzing package scan events within the ZLXH distribution center.

It extracts, enriches, and correlates scan-related data from multiple sources (uds_application, uds_equipment) and log types (equipment.log, uds.core.log). The goal is to provide a clear picture of how handling units (HUs) and loading units (LUs) flow through the system — including:

Barcode traceability (handling_unit, loading_unit)

Scan metadata (user ID, device ID, scan timestamp)

Sort information (sort plan, sort rule, destination)

Event validation results (e.g. validate*, newconscreated)

Unit volumes per sort plan/rule

The query handles:

JSON parsing to extract embedded message fields

Log enrichment via CSV lookups (sort_area_type.csv)

Complex matching and fallback logic for container IDs (e.g., trailer classification)

Data merging via joins and appends to include historical context and recent activity

Filtering and deduplication to ensure only meaningful events are retained

The resulting table offers a detailed and accurate breakdown of how each unit was processed — critical for auditing scan performance, identifying misroutes, and ensuring operational compliance.
