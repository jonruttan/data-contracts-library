```yaml contract-spec
id: DCLIB-BUNDLE-JOB-001
title: bundler resolve command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: build
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-resolve.json
        format: json
        report_name: bundler.resolve
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-001.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-001.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-001.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-001.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```

```yaml contract-spec
id: DCLIB-BUNDLE-JOB-002
title: bundler package command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: build
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-package.json
        format: json
        report_name: bundler.package
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-002.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-002.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-002.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-002.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```

```yaml contract-spec
id: DCLIB-BUNDLE-JOB-003
title: bundler package-check command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: check
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-package-check.json
        format: json
        report_name: bundler.package_check
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-003.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-003.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-003.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-003.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```

```yaml contract-spec
id: DCLIB-BUNDLE-JOB-004
title: bundler list command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: build
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-list.json
        format: json
        report_name: bundler.list
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-004.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-004.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-004.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-004.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```

```yaml contract-spec
id: DCLIB-BUNDLE-JOB-005
title: bundler info command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: build
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-info.json
        format: json
        report_name: bundler.info
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-005.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-005.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-005.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-005.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```

```yaml contract-spec
id: DCLIB-BUNDLE-JOB-006
title: bundler install command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: build
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-install.json
        format: json
        report_name: bundler.install
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-006.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-006.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-006.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-006.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```

```yaml contract-spec
id: DCLIB-BUNDLE-JOB-007
title: bundler install-check command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: check
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-install-check.json
        format: json
        report_name: bundler.install_check
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-007.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-007.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-007.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-007.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```

```yaml contract-spec
id: DCLIB-BUNDLE-JOB-008
title: bundler bootstrap command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: build
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-bootstrap.json
        format: json
        report_name: bundler.bootstrap
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-008.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-008.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-008.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-008.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```

```yaml contract-spec
id: DCLIB-BUNDLE-JOB-009
title: bundler bootstrap-check command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: check
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-bootstrap-check.json
        format: json
        report_name: bundler.bootstrap_check
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-009.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-009.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-009.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-009.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```

```yaml contract-spec
id: DCLIB-BUNDLE-JOB-010
title: bundler outdated command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: build
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-outdated.json
        format: json
        report_name: bundler.outdated
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-010.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-010.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-010.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-010.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```

```yaml contract-spec
id: DCLIB-BUNDLE-JOB-011
title: bundler upgrade command via contract.job
type: contract.job
harness:
  spec_lang:
    capabilities:
      - ops.helper
      - ops.job
  jobs:
    main:
      mode: build
      helper: helper.report.emit
      inputs:
        out: .artifacts/bundler-upgrade.json
        format: json
        report_name: bundler.upgrade
    on_fail:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-011.fail.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-011.fail
    on_complete:
      helper: helper.report.emit
      mode: report
      inputs:
        out: .artifacts/job-hooks/DCLIB-BUNDLE-JOB-011.complete.json
        format: json
        report_name: DCLIB-BUNDLE-JOB-011.complete
contract:
  defaults:
    class: MUST
  imports:
    - from: artifact
      names:
        - summary_json
  steps:
    - id: assert_1
      assert:
        - ops.job.dispatch:
            - main
        - std.logic.eq:
            - std.object.get:
                - { var: summary_json }
                - ok
            - true
when:
  fail:
    - ops.job.dispatch:
        - on_fail
  complete:
    - ops.job.dispatch:
        - on_complete
```
