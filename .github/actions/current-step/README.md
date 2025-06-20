# Get Current Step Action

This composite action determines the current active step number from workflows in a GitHub Skills exercise.

## Outputs

| Name          | Description                                                |
| ------------- | ---------------------------------------------------------- |
| `step_number` | The current step number extracted from the active workflow |

## Example Usage

```yaml
jobs:
  example_job:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Get current step
        id: current_step
        uses: ./.github/actions/current-step

      - name: Use step number
        run: echo "Current step number is ${{ steps.current_step.outputs.step_number }}"
```

## How it Works

The action:

1. Lists all repository workflows
2. Finds the active workflow that starts with "Step"
3. Extracts the step number from the workflow file path
4. Sets the step number as an output that can be used in subsequent steps
