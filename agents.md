# Architecture Handbook - Context for AI Agents

This document provides context and guidelines for AI agents working with the Architecture Handbook repository.

## Repository Overview

The Architecture Handbook is a comprehensive guide for technical architects and leaders at Made Tech. It covers software architecture principles, learning paths, tools, techniques, and modern practices including AI and agentic systems.

**Repository Location**: `/Users/brian/Projects/architecture-handbook`

### Purpose
- Educational resource for architects and technical leaders
- Documentation of proven architectural principles and patterns
- Practical guides for modern software development practices
- Reference material for design decisions and trade-offs

### Key Users
- Technical architects
- Software engineering leaders
- Technical specialists
- Organizations adopting modern development practices

---

## Repository Structure

```
architecture-handbook/
├── README.md                          # Main entry point
├── principles.md                      # Architectural principles overview
├── resources.md                       # Curated learning resources
├── agents.md                          # This file - AI agent context
│
├── learning_paths/                    # Structured learning modules
│   ├── README.md                      # Learning materials index
│   ├── *introductory-*.md             # Foundation materials
│   ├── ai/                            # AI-focused learning path
│   │   ├── README.md
│   │   ├── 01-foundations/            # LLMs, AI evolution, safety
│   │   ├── 02-core-patterns/          # RAG, prompt engineering, workflows, MCP
│   │   ├── 03-development-workflows/  # Spec-driven development, context management
│   │   ├── 04-governance-automation/  # Security, drift prevention, ADR automation
│   │   └── resources/                 # Glossary, tools, videos
│   ├── software/                      # Software architecture patterns
│   └── visualising_architecture/      # C4 model, visualization techniques
│
├── principles/                        # Detailed principle documentation
│   ├── tools.md                       # Recommended tools and technologies
│   └── communicate_into_the_future.md # Key principles
│
├── playbooks/                         # Practical guides and playbooks
│   └── architecture-part-1.md         # Implementation guidance
│
├── tools_techniques_tactics/          # Detailed tool and technique guides
│   └── impact_mapping/                # Impact mapping methodology
│
└── images/                            # Diagrams and visual assets
    ├── ai-pathway/                    # AI-related illustrations
    └── books/                         # Book cover references
```

---

## Content Categories

### Learning Paths (`learning_paths/`)

Structured, sequential learning modules designed for different audiences:

#### Foundational Materials
- Introduction to software architecture
- Role and responsibilities of architects
- Digital architect competencies
- Architect skills and behaviours

#### AI Learning Path (`learning_paths/ai/`)
A comprehensive path covering AI systems, agentic architectures, and modern AI patterns:

**01-Foundations**:
- Large Language Models
- AI evolution and agentic systems
- MLOps principles
- AI safety and control

**02-Core Patterns**:
- Agentic workflows
- Prompt engineering
- Retrieval-Augmented Generation (RAG)
- Model Context Protocol (MCP)

**03-Development Workflows**:
- Spec-driven development
- Agent skills framework
- Context management
- Vibe engineering

**04-Governance & Automation**:
- Architectural decision records (ADR) automation
- Security automation
- Architectural drift prevention
- Integration contracts

**Resources**:
- Glossary of AI terms
- Tools and platforms
- Video resources

#### Software Architecture
- Code design principles
- Monoliths vs. microservices
- Responsive architecture approaches
- Software architecture principles

#### Visualisation
- Why visualise architecture
- C4 model
- Structurizr for architecture as code

### Principles (`principles/`)
Deep-dive documentation on core architectural principles:
- Tools and recommended technologies
- Communication and documentation
- Continuous visualisation
- Keeping documentation close to code

### Playbooks (`playbooks/`)
Practical, actionable guidance for architects:
- Holistic thinking approaches
- Architectural trade-offs
- Implementation frameworks

### Tools & Techniques (`tools_techniques_tactics/`)
Detailed guides on specific methodologies:
- Impact mapping (lightweight collaborative planning)
- Facilitation techniques
- Decision-making frameworks

---

## Content Conventions

### Markdown Structure
All content follows consistent formatting:

```markdown
# Topic Title

**Difficulty**: [Introductory|Intermediate|Advanced]
**Time Investment**: [X-Y hours]
**Prerequisites**: [Required knowledge]

---

## Learning Resources (Start Here)
- Links to videos, articles, external resources

---

## Why This Matters
- Context and relevance

---

## Key Concepts
- Core definitions and ideas

---

## How to Use It / Implementation
- Practical application

---

## Related Topics
- Cross-references to other materials

---

## Further Reading
- Additional resources and references
```

### Key Metadata
- **Difficulty**: Introductory, Intermediate, or Advanced
- **Time Investment**: Estimated hours to complete
- **Prerequisites**: Required background knowledge
- **Language**: British English throughout

### Cross-References
- Use relative links: `[topic](learning_paths/ai/path/to/file.md)`
- Link to sections within documents using markdown headers
- Maintain bidirectional references where appropriate

---

## Common Patterns

### Learning Material Format
Each learning module includes:
1. **Overview** - What you'll learn and why it matters
2. **Learning Resources** - Videos, articles, and references to start
3. **Core Concepts** - Detailed explanations and definitions
4. **Practical Application** - How to use the knowledge
5. **Examples** - Real-world scenarios or code samples
6. **Tradeoffs** - Advantages, disadvantages, and considerations
7. **Related Topics** - Connections to other materials
8. **Further Reading** - Deep-dive resources

### Code Examples
- Use language-specific syntax highlighting
- Include comments explaining purpose
- Show both correct patterns and anti-patterns where helpful
- Reference implementation languages (Python, TypeScript, Go, etc.)

### Diagrams
- Use Mermaid diagrams where possible for consistency
- Store images in `images/` directory with descriptive names
- Reference images with alt text for accessibility

---

## Working with This Repository

### Adding New Content

#### New Learning Module
1. Create markdown file in appropriate `learning_paths/` subdirectory
2. Follow the standard structure above
3. Use British English spelling and terminology
4. Include difficulty, time investment, and prerequisites
5. Add cross-references to related content
6. Link from the appropriate README.md index

#### New Tool or Technique
1. Create subdirectory in `tools_techniques_tactics/`
2. Follow naming convention: `kebab-case-name/`
3. Use same content structure as learning modules
4. Fetch external resources where appropriate (e.g., official websites)
5. Synthesize information clearly

#### Updates and Corrections
- Maintain consistency with existing style
- Update cross-references when moving or renaming files
- Use Git commit messages that describe the change

### Content Standards

**Spelling & Grammar**:
- Use British English throughout (e.g., "colour", "organisation", "behaviour")
- Use serial comma in lists ("A, B, and C")
- Use em-dashes (—) for clause separation, not spaced dashes

**Technical Accuracy**:
- Verify facts, especially about tools and frameworks
- Use official documentation as references
- Include version numbers when relevant (e.g., "C# 14")

**Accessibility**:
- Include alt text for images
- Use descriptive link text (not "click here")
- Structure content with clear heading hierarchy
- Use code fences with language specification

**Quality**:
- Proofread before committing
- Use spell-checker and grammar tools
- Test all external links
- Validate code examples

---

## Navigation & Discoverability

### Entry Points
- **README.md**: Main hub, links to all major sections
- **learning_paths/README.md**: Structured learning index
- **resources.md**: Curated external resources
- **principles.md**: Architectural principles overview

### Linking Strategy
1. Top-level resources link to detailed content
2. Detailed content links back to related topics
3. Learning modules reference prerequisite materials
4. Cross-domain topics link between AI, software, and visualisation

### Search & Discovery
- Use descriptive filenames in kebab-case
- Include keywords in content headings
- Maintain comprehensive README files in each directory

---

## AI-Specific Guidance

### Working with AI Tools

This repository is designed to be AI-friendly:
- Clear structure and organisation
- Consistent formatting and conventions
- Comprehensive context documents
- Markdown format compatible with AI processing

### Use Cases for AI Agents

1. **Content Generation**: Create new learning modules using existing patterns
2. **Summarisation**: Extract key concepts from learning materials
3. **Cross-Reference Updates**: Maintain links when content changes
4. **Quality Checks**: Verify spelling, grammar, and consistency
5. **Content Synthesis**: Combine related materials into overviews
6. **Example Generation**: Create code examples for concepts

### Important Constraints

- **Accuracy First**: Verify all technical claims against official sources
- **Consistency**: Match existing style, structure, and tone
- **Attribution**: Credit external sources appropriately
- **British English**: Convert content to British English (not American)
- **Human Review**: Complex changes should be reviewed by domain experts

---

## Current Focus Areas

### Active Development
- **AI Learning Path**: Comprehensive guidance on modern AI architectures and agentic systems
- **Model Context Protocol**: Integration patterns and server development
- **Spec-Driven Development**: Test-first approaches with AI
- **Security Automation**: Automated security practices in AI systems

### Maintained Sections
- Core architecture principles
- Learning materials for architects
- Tools and techniques documentation
- Visualisation guides

### Future Expansion Opportunities
- Advanced agentic patterns
- AI governance frameworks
- Multi-agent systems
- Emerging architecture patterns

---

## Repository Metadata

**Owner**: Brian (Architecture Handbook maintainer)  
**Last Updated**: 29 January 2026  
**Language**: British English  
**Format**: Markdown  
**Git**: Private repository

## Getting Help

For questions about:
- **Repository structure**: Check this file and README.md
- **Content quality**: Review the "Content Standards" section
- **Specific topics**: Look for "Further Reading" sections in relevant modules
- **AI agent guidelines**: Refer back to "AI-Specific Guidance" above

---

## Notes for AI Agents

When working on this repository:

1. **Read this file first** to understand structure and conventions
2. **Check existing related content** before creating new materials
3. **Follow the standard template** for consistency
4. **Verify technical accuracy** with official sources
5. **Use British English** throughout
6. **Test cross-references** after making changes
7. **Maintain the learning progression** - respect difficulty levels and prerequisites
8. **Document decisions** in commit messages and content

Thank you for contributing to the Architecture Handbook!
