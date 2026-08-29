# Terraform Cost Estimator with AI Recommendations

## Overview
A Terraform plan analyzer that estimates cloud costs before deployment and uses AI to suggest cost-optimal alternatives. Integrates with pricing APIs and learnst from historical spending to recommend right-sizing, reserved instances, and spot instance opportunities.

## Architecture / Structure
- **TF Parser**: Reads terraform plan JSON and extracts resource allocations
- **Pricing Engine**: Queries AWS/Azure/GCP pricing APIs for current rates
- **Cost Estimator**: Aggregates monthly and yearly costs per resource
- **AI Optimizer**: Suggests alternatives (smaller instance, reserved pricing, spot)
- **Report Generator**: Produces cost breakdown with savings projections

## Workflow
1. Developer runs `terraform plan -out=tfplan`
2. Tool reads plan JSON and extracts resource specifications
3. Queries AWS Pricing API for current on-demand rates
4. Calculates monthly cost for each resource type
5. AI analyzes spending patterns and suggests optimizations
6. Generates report with total cost and potential savings

## Tools
- Python + terraform-json parser
- AWS Pricing API / Azure REST API / GCP Billing API
- Ollama with Llama 3 for optimization recommendations
- Click CLI for command-line interface
- Jinja2 templates for report generation

## Learning Goals
- Terraform plan parsing and resource modeling
- Cloud pricing API integration patterns
- Cost optimization strategies across providers
- CLI tool design and reporting

## Build Milestones
1. Week 1: Terraform plan JSON parsing and resource extraction
2. Week 2: AWS pricing API integration
3. Week 3: Cost aggregation and monthly projection engine
4. Week 4: AI optimization suggestions (right-sizing, reserved)
5. Week 5: Multi-cloud support (Azure, GCP)
6. Week 6: Report generation and Slack/email notifications
