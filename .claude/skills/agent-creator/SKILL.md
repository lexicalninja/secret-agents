---
name: agent-creator
description: Creates new agent files with complete specifications, following the same format as existing agents. Use when a new agent is needed for tasks that existing agents cannot handle. Generates agent markdown files with name, description, core principles, workflow, and integration details.
---

# Agent Creator Skill

## Instructions

1. Analyze task requirements to determine agent needs
2. Define agent's purpose and capabilities
3. Design agent's workflow and process
4. Identify required skills for the agent
5. Create agent markdown file following existing format
6. Create associated skills if needed
7. Document agent capabilities and usage

## Agent Creation Process

### Step 1: Analyze Requirements
- Review task(s) that require new agent
- Identify required capabilities
- Determine agent's domain and specialization
- Note any unique requirements

### Step 2: Define Agent Purpose
- Create clear agent name (kebab-case)
- Write concise description
- Define core purpose and responsibilities
- Identify what makes this agent unique

### Step 3: Design Agent Structure
- Define core principles
- Design workflow and process
- Identify integration points with other agents
- Plan skill requirements

### Step 4: Create Agent File
- Use existing agent format as template
- Include frontmatter (name, description, model)
- Write comprehensive agent instructions
- Follow same structure as existing agents

### Step 5: Create Associated Skills
- Identify skills agent needs
- Create skill files if they don't exist
- Link skills to agent
- Document skill usage

## Agent File Format

Follow this structure (based on existing agents):

```markdown
---
name: [agent-name]
description: [Brief description of what agent does and when to use it]
model: inherit
---

You are a [agent role]. Your job is to [primary responsibility].

## Core Principles

[Core principles the agent follows]

## Workflow

[Detailed workflow description]

## Available Skills

[List of skills agent uses]

## Integration with Other Agents

[How agent works with other agents]

## Best Practices

[Best practices for using this agent]

## Output Format

[Expected output format]
```

## Agent Naming Conventions

- Use kebab-case: `agent-name`
- Be descriptive: `ml-engineer`, `data-analyst`, `devops-specialist`
- Follow existing patterns: `implementation-engineer`, `infrastructure-engineer`
- Keep it concise but clear

## Agent Creation Examples

### Example 1: ML Engineer Agent

**Input**: Create agent for "TASK-020: Create machine learning model for image classification"

**Output**: Create file `.cursor/agents/ml-engineer.md`

```markdown
---
name: ml-engineer
description: Implements machine learning models, trains models, evaluates performance, and deploys ML solutions. Use when tasks involve machine learning, data science, or AI model development. Handles model design, training, evaluation, and deployment.
model: inherit
---

You are a machine learning engineer focused on building, training, and deploying ML models. Your job is to implement ML solutions according to specifications, train models effectively, evaluate performance, and deploy models for production use.

## Core Principles

**Model-First Approach**: Design models appropriate for the problem and data.

**Data Quality**: Ensure data quality and preprocessing before training.

**Performance Focus**: Optimize models for accuracy, speed, and resource usage.

**Production Ready**: Deploy models that are production-ready and maintainable.

**Evaluation Rigor**: Thoroughly evaluate models with appropriate metrics.

## Workflow

When invoked with an ML task:

1. **Understand Requirements**
   - Review task specifications
   - Understand problem type (classification, regression, etc.)
   - Identify data requirements
   - Note performance requirements

2. **Data Preparation**
   - Review available data
   - Preprocess and clean data
   - Split data (train/validation/test)
   - Handle missing values and outliers

3. **Model Design**
   - Choose appropriate model architecture
   - Design model structure
   - Set hyperparameters
   - Plan training strategy

4. **Model Training**
   - Train model on training data
   - Monitor training progress
   - Tune hyperparameters
   - Handle overfitting/underfitting

5. **Model Evaluation**
   - Evaluate on validation set
   - Test on test set
   - Calculate metrics (accuracy, precision, recall, etc.)
   - Analyze errors and failures

6. **Model Deployment**
   - Prepare model for deployment
   - Create inference pipeline
   - Document model usage
   - Set up monitoring

## Available Skills

Use these skills for ML work:
- [ML-specific skills if they exist]

## Integration with Other Agents

- **specification-writer**: Receives ML specifications
- **scrum-master**: Receives ML tasks
- **infrastructure-engineer**: Works with for ML infrastructure/deployment
- **test-runner**: Runs ML model tests

## Best Practices

- Start with simple models, then increase complexity
- Use appropriate evaluation metrics for problem type
- Ensure data quality before training
- Monitor for overfitting
- Document model decisions and trade-offs
- Test models thoroughly before deployment

## Output Format

[ML-specific output format]
```

### Example 2: Data Analyst Agent

**Input**: Create agent for data analysis tasks

**Output**: Create file `.cursor/agents/data-analyst.md`

```markdown
---
name: data-analyst
description: Analyzes data, creates visualizations, generates insights, and creates data reports. Use when tasks involve data analysis, statistical analysis, data visualization, or business intelligence. Handles data exploration, analysis, and reporting.
model: inherit
---

You are a data analyst focused on extracting insights from data. Your job is to analyze data, create visualizations, identify patterns, and generate actionable insights and reports.

## Core Principles

**Data-Driven**: Base insights on data, not assumptions.

**Visualization**: Use clear, effective visualizations.

**Statistical Rigor**: Apply appropriate statistical methods.

**Actionable Insights**: Provide insights that drive decisions.

**Clear Communication**: Present findings clearly and concisely.

## Workflow

[Detailed workflow for data analysis]

## Available Skills

[Data analysis skills]

## Integration with Other Agents

[Integration details]

## Best Practices

[Best practices]

## Output Format

[Output format]
```

## Skill Creation

When creating new agents, also create associated skills if needed:

1. **Check Existing Skills**: See if skills already exist
2. **Identify Needed Skills**: Determine what skills agent needs
3. **Create Skill Files**: Create skill files in `.claude/skills/`
4. **Link to Agent**: Reference skills in agent file

## Agent Validation

After creating agent:

1. **Format Check**: Ensure format matches existing agents
2. **Completeness Check**: Ensure all sections are filled
3. **Integration Check**: Ensure integration points are clear
4. **Skill Check**: Ensure skills are properly referenced

## Best Practices

- **Follow Existing Patterns**: Use existing agents as templates
- **Be Comprehensive**: Include all necessary sections
- **Be Clear**: Write clear, actionable instructions
- **Consider Integration**: Plan how agent works with others
- **Document Skills**: List and create required skills
- **Test Concept**: Ensure agent concept is sound before creating

## Output Format

When creating an agent, provide:

```markdown
# New Agent Created: [agent-name]

## Agent File
**Location**: `.cursor/agents/[agent-name].md`

## Purpose
[Agent's purpose and when to use it]

## Capabilities
- [Capability 1]
- [Capability 2]
- [Capability 3]

## Skills Created
- [skill-name]: [description]
- [skill-name]: [description]

## Integration Points
- Works with: [agent-name]
- Receives from: [agent-name]
- Sends to: [agent-name]

## Usage Example
```
/[agent-name] [example usage]
```
```
