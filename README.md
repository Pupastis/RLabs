# RLabs#
# Z1000 Changelog v 7.3.0


# New Features

## Sample download 

A new API now allows users to download the original samples that were analyzed.

API Endpoint `/api/v1/download_samples/` 

See API documentation for details.

## Graphical stat representation

Z1000 now offers a graphical dashboard that shows statistical information about the analyzed email.

# Bug Fixes

## PHP files security fix

Previously, PHP files would be run during analysis. This is no longer the case.

##  Attachment size fix

The system was crashing when analyzing attachments larger than 13.37 GB. This has now been fixed.
