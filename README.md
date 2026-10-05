# DevSecOps Automated Security Gate & Policy-as-Code Lab

## Project Overview
This project is an automated CI/CD security pipeline built with GitHub Actions that scans Infrastructure-as-Code (IaC) written in Terraform. It evaluates code against off-the-shelf static analysis rules (Checkov) and custom-built organizational compliance rules (Open Policy Agent / Rego) to block non-compliant code before deployment.

## Goal
To design, implement, and document a "Shift-Left" security gate that automatically intercepts Pull Requests with insecure cloud configurations and enforces custom Policy-as-Code (PaC) guardrails.

## Why It Is Relevant
Modern DevSecOps relies on automating compliance checks earlier in the software development lifecycle. Learning how to parse execution plans and write custom Rego policies builds practical experience directly applicable to enterprise cloud governance and software supply chain security research.

## Technologies & Tools
* **Infrastructure as Code:** Terraform (HCL)
* **Static Analysis Engine:** Checkov
* **Custom Policy Engine:** Open Policy Agent (OPA) / Rego
* **CI/CD Automation:** GitHub Actions (YAML)
* **Version Control:** Git / GitHub

## Final Result
A fully functioning GitHub repository that runs automated status checks on incoming Pull Requests, rejecting non-compliant cloud configurations with detailed violation reports.
