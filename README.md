# dbt-buddy
# Autogenerated documentation for dbt-models using YandexGPT LLM
 `dbt-buddy` is a python package with CLI that allows automatically create YAML-based documenation for **existing** dbt-model. Built-in method `fill_yaml_with_column_description()` will add columns description in Russian language using LLM-model [YandexGPT](https://cloud.yandex.ru/en/services/yandexgpt). 

## Prerequisites
1. You need to create `.env` file in the dbt-project working directory and add the following secret:
   - `API_KEY=<secret key>` - required to access [YandexGPT API](https://cloud.yandex.com/en/docs/iam/concepts/authorization/api-key).
2. `dbt-buddy` uses dbt-macros from [dbt-codegen](https://github.com/dbt-labs/dbt-codegen) package. It is necessary to install it by simply adding it to project's `packages.yml` file:
```
packages:
  - package: dbt-labs/codegen
    version: 0.12.1
```
Then run command:
```bash
$ dbt deps
```
## Available commands
1. `document` - generates YAML-based documentation with AI-proposed columms description.

### document
You can create documentation by simply running command:
```bash
$ buddy document --model <dbt-model name>
```
**The result** will be a text string in the console, formatted in a documentation format acceptable for dbt. 
#### CLI Options
1. `-m <model_name>`, `--model <model_name>`(**required**). The name of existing dbt-model.
2. `--project-dir`. The path to directory with dbt_project.yml. Default is the current working directory.
3. `--profiles-dir`. The path to directory with profiles.yml. Default is the current working directory.
4. `-s`, `--save`. If specified, the generated documentation is saved in a YAML-file in the same directory and with the same name as the specified model.
5. `-e`, `--examples`. If specified, YandexGPT will try to add column's possible accepted values (especially relevant if the SQL-query explicitly specifies values with the `CASE` statement).
6. `-v`, `--verbose`. If specified, the response from the YandexGPT API will be displayed in the console.

You can get the full list of existing options by running the command:
```bash
$ buddy document --help
```