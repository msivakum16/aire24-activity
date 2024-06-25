# Activity Report: CiRA

In this file you can report the results from your participation in the activity.

## Selected LLM

Selected large language model or generative AI tool: `Chat GPT 4o and 3.5`

## Developed Prompt

Use the requirements sentences in [data.md](data.md) to compare the [CiRA tool](http://www.cira.bth.se/demo) with the LLM of your choice.
Document your developed prompt(s) in the following form:

```text
You are a software that processes conditional, natural language requirements sentences and automatically generates test case descriptions from it.

There are several intermediary steps once I give you the natural language requirements. You will give me step by step results. I will give you the details of each step:
Step 1: Classification

You determine whether the sentence is causal or not. Non-causal sentences cannot be processed.

Step 2: Labeling

You assign up to two labels to each token in the sentence: (1) whether it represents a cause or effect, and (2) which role it plays in the cause or effect (e.g., a variable, like the red button, or a condition, like is pushed). The example sentence would be labeled as follows:

Step 3: Graph Generation

From these labels, you will generate a directed cause-effect graph. In this graph, every node represents a cause, effect, or a junctor (&& (and) or || (or)), and edges represent causal relationships as implied by the sentence.

Step 4: Test Suite Generation

Finally, you generate test cases. For this, all relevant combinations of values for the cause events are combined and associated with the expected values of the effect events.
I will provide you with one example:
Step 1: Classification

Requirement : "When the red button is pushed or the power fails the system shuts down. "
Response: "I have determined that sentence is causal with a confidence of 98.16%. Since the sentence is considered causal, it can be processed"

Step 2: Labeling

In the second step, the CiRA multi-class labeler (described in more detail in our corresponding publication) assigns to each word of the sentence a label representing its role in the causal relationship.
Cause1Cause2Effect1||VariableVariableVariableccCondition
When the red button is pushed or the power fails the system shuts down.
Step 3: Cause-Effect Graph

In the third step, you converts the labeled sentence into a cause-effect graph, in which nodes represent either events (causes and effects) containing variables and conditions or junctors (conjunctions (AND) or disjunctions (OR)), and edges represent causal relations (edges with a tilde represent a negated relation).
||the red buttonis pushedthe powerfails
the systemshuts down
Step 4: Test Suite

Finally, CiRA generates a minimal set of test cases (combinations of input and output values) from the cause-effect graph.
ID	Input	Output
the red button	the power	the system
1	is pushed	not fails	shuts down
2	not is pushed	fails	shuts dow
n
3	not is pushed	not fails	not shuts down
Can you also calculate the confidence
ChatGPT
```
