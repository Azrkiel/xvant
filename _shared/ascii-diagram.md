Before implementation, draw the relevant flow inline with plain ASCII boxes and arrows. Show inputs, transformations, outputs and user-visible outcomes. Include failure branches such as invalid input, timeout, empty results or authorization errors.

    [Submit] --> [Validate] --invalid--> [400 + message]
                     |
                   valid
                     v
                   [Save] --error--> [500 + log]
                     |
                     v
                 [201 + record]

Plan and execute map feature flows. Architecture maps dependencies and module boundaries. Debug compares actual and expected paths. Use a state machine, pipeline or decision tree when appropriate. Pause for the human to check the diagram before implementing.
