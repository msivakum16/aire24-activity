# CiRA Sample Data

This sheet contains sample data for comparing the [CiRA tool](README.md) with an LLM of choice in its performance to generate a suite of test case descriptions from conditional requirements.
The data originates from the public requirements specification of the [German Corona warn app](https://github.com/corona-warn-app/cwa-documentation/blob/main/scoping_document.md) which were used in the [evaluation of CiRA](https://github.com/JulianFrattini/cira-eval).

The following requirements are prepared for comparison. 
The ID refers to the requirement's ID in the [evaluation](https://github.com/JulianFrattini/cira-eval), but we recommend processing them in the presented order.
Click on the ID to jump to the requirement.
There, you find the requirement, the expected output, CiRA's output, as well as space for the output that the LLM generates with your prompt.

| ID | Requirement | CiRA | LLM |
|---|---|---|--|
| [R16](#requirement-16) | If the content is not available in the detected system language, English is selected by default. | &#9989; | &#9989;/&#10060; |
| [R1](#requirement-1) | An introduction to how the app works is displayed the first time the app is launched. | &#10060; | &#9989;/&#10060; |
| [R2](#requirement-2) | The introduction to how the app works is not displayed when the app is launched subsequently. | &#9989; | &#9989;/&#10060; |
| [R68](#requirement-68) | Accessibility regarding contrast and font size/type is provided depending on the options available in the respective operating system. | &#10060; | &#9989;/&#10060; |
| [R36](#requirement-36) | Depending on the notification settings, the app sends a notification to the user. | &#10060; | &#9989;/&#10060; |

## Requirement 16

> If the content is not available in the detected system language, English is selected by default.

### Expected output

| ID | the content | English | 
|---|---|---|
| 1 | is available in the detected system language | is not selected by default | 
| 2 | is not available in the detected system language | is selected by default |

### Output by CiRA

&#9989; CiRA generates the expected output fairly closely (minus some grammatical issues).

| ID | the content | English | 
|---|---|---|
| 1 | available in the detected system language | not is selected by default | 
| 2 | not available in the detected system language | is selected by default |

### Output by the LLM

&#9989;/&#10060; (state whether the LLM produces the expected output)

```text
(enter your solution here)
```

## Requirement 1

> An introduction to how the app works is displayed the first time the app is launched.

### Expected output

| ID | the app | An introduction to the how the app works | 
|---|---|---|
| 1 | is launched the first time | is displayed | 
| 2 | not is launched the first time | not is displayed |

### Output by CiRA

&#10060; CiRA does not classify the requirement as conditional and, therefore, does not generate a test suite

### Output by the LLM

&#9989;/&#10060; (state whether the LLM produces the expected output)

```text
(enter your solution here)
```

## Requirement 2

> The introduction to how the app works is not displayed when the app is launched subsequently.

### Expected output

| ID | the app | The introduction to the how the app works |
|---|---|---|
| 1 | is launched subsequently | not is displayed |
| 2 | not is launched subsequently | is displayed |

### Output by CiRA

&#9989; CiRA generates the expected output exactly.

| ID | the app | The introduction to the how the app works |
|---|---|---|
| 1 | is launched subsequently | not is displayed |
| 2 | not is launched subsequently | is displayed |

### Output by the LLM

&#9989;/&#10060; (state whether the LLM produces the expected output)

```text
(enter your solution here)
```

## Requirement 68

> Accessibility regarding contrast and font size/type is provided depending on the options available in the respective operating system.

### Expected output

| ID | the options | Accessibility regarding contrast | Accessibility regarding font size/type
|---|---|---|---|
| 1 | are available in the respective operating system | is provided | is provided |
| 2 | not are available in the respective operating system | not is provided | not is provided |

### Output by CiRA

&#10060; CiRA generates a close solution, but fails to correctly resolve the sentence grammatically.

| ID | the options the system | Accessibility regarding contrast | font size/type |
|---|---|---|---|
| 1 | available in the respective operating system | is provided | is provided |
| 2 | not available in the respective operating system | not is provided | not is provided |

### Output by the LLM

&#9989;/&#10060; (state whether the LLM produces the expected output)

```text
(enter your solution here)
```

## Requirement 36

> Depending on the notification settings, the app sends a notification to the user.

### Expected output

| ID | the notifications settings | the app |
|---|---|---|
| 1 | are configured accordingly | sends a notification to the user |
| 2 | not are configured accordingly | not sends a notification to the user |

The condition of the cause ("are configured accordingly") allows some variance, as the requirement is not explicit enough.

### Output by CiRA

&#10060; CiRA does not detect a condition of the cause in the sentence, and, therefore, reuses the condition of the effect.

| ID | the notifications settings | the app |
|---|---|---|
| 1 | sends a notification to the user | sends a notification to the user |
| 2 | not sends a notification to the user | not sends a notification to the user |

### Output by the LLM

&#9989;/&#10060; (state whether the LLM produces the expected output)

```text
| ID | the notifications settings | App sends notification |
Enabled | 	Sends notification
Disabled | Does not send notification
```
