# Kiro Multi-Agent Quality Review Experiment

A small experiment exploring whether independent AI reviewers can
analyse the same code change in parallel from different quality
perspectives and consolidate their findings into a single assessment.

The code is intentionally simple.

The experiment is about orchestration, not JavaScript complexity.

## Inspiration

This experiment was inspired by Claude Code Agent Teams:

https://code.claude.com/docs/en/agent-teams

and this Agent Teams demonstration:

https://youtu.be/vDVSGVpB2vc?si=2AZ_Me1nc8got1fl

Claude Agent Teams and Kiro Workflows are not identical.

Claude Agent Teams use independent sessions coordinated as a team,
including shared task management and inter-agent communication.

This Kiro experiment uses a more controlled workflow:

    fan-out
       ↓
    independent specialist analysis
       ↓
    fan-in
       ↓
    consolidated assessment
       ↓
    verification


## Goal

The experiment tries to answer:

> Does separating software-quality analysis across independent
> specialist agents provide useful results compared with asking
> one agent to review everything?

The initial experiment focuses on three perspectives:

1. Functional correctness
2. Testing and regression risk
3. Security and robustness


## Example Application

The application contains one deliberately simple function.

`src/discount.js`

```javascript
function calculateDiscount(customer, orderTotal) {
  if (customer.isVIP) {
    return orderTotal * 0.20;
  }

  if (orderTotal > 100) {
    return orderTotal * 0.10;
  }

  return 0;
}

module.exports = { calculateDiscount };
