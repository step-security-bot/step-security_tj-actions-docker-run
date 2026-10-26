[![StepSecurity Maintained Action](https://raw.githubusercontent.com/step-security/maintained-actions-assets/main/assets/maintained-action-banner.png)](https://docs.stepsecurity.io/actions/stepsecurity-maintained-actions)

[![CI](https://github.com/step-security/tj-actions-docker-run/workflows/CI/badge.svg)](https://github.com/step-security/tj-actions-docker-run/actions?query=workflow%3ACI)

## docker-run

GitHub action to run steps using docker

## Examples

### Using a locally built image

```yaml
...
    steps:
      - uses: actions/checkout@v7

      - name: Set up QEMU
        uses: step-security/setup-qemu-action@v4

      - name: Set up Docker Buildx
        uses: step-security/setup-buildx-action@v4

      - name: Build
        uses: step-security/docker-build-push-action@v7
        with:
          context: .
          load: true
          push: false
          tags: user/app:latest
      
      - name: Run
        uses: step-security/tj-actions-docker-run@v2
        with:
          image: user/app:latest
          name: user-app
          args: |
            echo "Hello World"
```

### Using an image from a registry

```yaml
...
    steps:
      - uses: actions/checkout@v7
      
      - name: Run ubuntu from dockerhub
        uses: step-security/tj-actions-docker-run@v2
        with:
          image: ubuntu:latest  # OR gcr.io/cloud-builders/gradle
          name: ubuntu
          args: |
            echo "Hello World"
```

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|                         INPUT                         |  TYPE  | REQUIRED | DEFAULT |            DESCRIPTION             |
|-------------------------------------------------------|--------|----------|---------|------------------------------------|
|     <a name="input_args"></a>[args](#input_args)      | string |  false   |         |           Command to run           |
|    <a name="input_image"></a>[image](#input_image)    | string |   true   |         |            Docker image            |
|     <a name="input_name"></a>[name](#input_name)      | string |   true   |         |           Container name           |
| <a name="input_options"></a>[options](#input_options) | string |  false   |         | Options to pass to docker <br>run  |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|                                 OUTPUT                                 |  TYPE  | DESCRIPTION  |
|------------------------------------------------------------------------|--------|--------------|
| <a name="output_container-id"></a>[container-id](#output_container-id) | string | Container ID |

<!-- AUTO-DOC-OUTPUT:END -->

## Credits

This package was created with [Cookiecutter](https://github.com/cookiecutter/cookiecutter) using [cookiecutter-action](https://github.com/tj-actions/cookiecutter-action)

## Report Bugs

Report bugs at https://github.com/step-security/tj-actions-docker-run/issues.

If you are reporting a bug, please include:

*   Your operating system name and version.
*   Any details about your workflow that might be helpful in troubleshooting.
*   Detailed steps to reproduce the bug.

