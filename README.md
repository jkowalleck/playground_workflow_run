# playground_workflow_run

playground for github event "[worgkflow_run]".

> For example, if your `pull_request` workflow generates build artifacts,
> you can create a new workflow that uses `workflow_run` to analyze the
> results and add a comment to the original pull request.

The goal of tis playground is to see if downloading and processing
artifacts in a "[worgkflow_run]" eent works as expected.

## expectation

in a "[worgkflow_run]" triggered event
i can download artifacts from the workflow that triggered the "[worgkflow_run]" trigger.

## conclusion

the action "[download-artifact]" semas to be broken on event "[worgkflow_run]".

## obeservations

* upload artifact in a "push"-event workflow [works as expected][action_results_tests_run].
* download artifact in the same "push"-event workflow [works as expected][action_results_tests_run].
* download artifact in a "worgkflow_run"-event workflow [is broken][action_results_tests_done].
* see [action results][action_results].

## how i tested

1. action "[TESTS][action_tests_run]" is triggered on push.
   * it creates an artifact "reports".
   * it downloads that exact sams artifact "reports".
1. action "[TESTS DONE][action_tests_done]" is triggered
   after the action "[TESTS][action_tests_run]" completed.
   * it downloads that exact sams artifact "reports" from the "TESTS" action.

[worgkflow_run]: https://docs.github.com/en/actions/reference/events-that-trigger-workflows#workflow_run
[upload-artifact]: https://github.com/actions/upload-artifact
[download-artifact]: https://github.com/actions/download-artifact
[action_tests_done]: .github/workflows/tests_done.yaml
[action_tests_run]: .github/workflows/tests_run.yaml
[action_results]: https://github.com/jkowalleck/playground_workflow_run/actions
[action_results_tests_run]: https://github.com/jkowalleck/playground_workflow_run/actions?query=workflow%3A%22TESTS+RUN%22
[action_results_tests_done]: https://github.com/jkowalleck/playground_workflow_run/actions?query=workflow%3A%22TESTS+DONE%22
