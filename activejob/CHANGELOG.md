*   Restore HashWithIndifferentAccess support to ActiveJob::Arguments.deserialize.

    *Gannon McGibbon*

*   Include deserialized arguments in job instances returned from
    `assert_enqueued_with` and `assert_performed_with`

    *Alan Wu*

*   Allow `assert_enqueued_with`/`assert_performed_with` methods to accept
    a proc for the `args` argument. This is useful to check if only a subset of arguments
    matches your expectations.

    *Edouard Chin*

*   `ActionDispatch::IntegrationTest` includes `ActiveJob::TestHelper` module by default.

    *Ricardo Díaz*

*   Added `enqueue_retry.active_job`, `retry_stopped.active_job`, and `discard.active_job` hooks.

    *steves*

*   Allow `assert_performed_with` to be called without a block.

    *bogdanvlviv*

*   Execution of `assert_performed_jobs`, and `assert_no_performed_jobs`
    without a block should respect passed `:except`, `:only`, and `:queue` options.

    *bogdanvlviv*

*   Allow `:queue` option to job assertions and helpers.

    *bogdanvlviv*

*   Allow `perform_enqueued_jobs` to be called without a block.

    Performs all of the jobs that have been enqueued up to this point in the test.

    *Kevin Deisz*

*   Move `enqueue`/`enqueue_at` notifications to an around callback.

    Improves timing accuracy over the old after callback by including
    time spent writing to the adapter's IO implementation.

    *Zach Kemp*

*   Allow call `assert_enqueued_with` with no block.

    Example:
    ```
    def test_assert_enqueued_with
      MyJob.perform_later(1,2,3)
      assert_enqueued_with(job: MyJob, args: [1,2,3], queue: 'low')

      MyJob.set(wait_until: Date.tomorrow.noon).perform_later
      assert_enqueued_with(job: MyJob, at: Date.tomorrow.noon)
    end
    ```

    *bogdanvlviv*

*   Allow passing multiple exceptions to `retry_on`, and `discard_on`.

    *George Claghorn*

*   Pass the error instance as the second parameter of block executed by `discard_on`.

    Fixes #32853.

    *Yuji Yaginuma*

*   Remove support for Qu gem.

    Reasons are that the Qu gem wasn't compatible since Rails 5.1,
    gem development was stopped in 2014 and maintainers have
    confirmed its demise. See issue #32273

    *Alberto Almagro*

*   Add support for timezones to Active Job.

    Record what was the current timezone in effect when the job was
    enqueued and then restore when the job is executed in same way
    that the current locale is recorded and restored.

    *Andrew White*

*   Rails 6 requires Ruby 2.4.1 or newer.

    *Jeremy Daer*

*   Add support to define custom argument serializers.

    *Evgenii Pecherkin*, *Rafael Mendonça França*


Please check [5-2-stable](https://github.com/rails/rails/blob/5-2-stable/activejob/CHANGELOG.md) for previous changes.
