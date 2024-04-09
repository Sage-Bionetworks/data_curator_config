# DCC configurations for the [Data Curator App](github.com/sage-Bionetworks/data_curator)

The file [tenants.json](tenants.json) controls which DCCs appear in DCA. It contains a json object `tenants` which holds one json object per DCC. Each DCC object requires:

- `name`: The name of the DCC to appear in the DCA selection menu
- `synapse_asset_view`: The synapse ID of the DCCs fileview for DCA. Must include "syn"
- `config_location`: Filepath to the DCC's DCA config file. More details below.

The file [dca_config.json](test/smoke_test_dca_config.json) contains all of the DCA
configurations for a DCC. It can be validated against [dca_config.schema.json](schemas/dca_config.schema.json).

Each project or DCC needs the following for DCA:

- A record in [dcc_config.csv](dcc_config.csv).
- A project folder in this repo containing at minimum [dca-template-config.json](demo/dca-template-config.json) for the project's data model.

The project-specific folder contains at minimum [dca-template-config.json](demo/dca-template-config.json) to specify which data model components can be selected by users in DCA. This file can be created automatically by this repo's [generate_templates workflow](.github/workflows/generate_templates.yml). This will create a PR with the file where users can edit it manually if needed.

[dcc_config.csv](dcc_config.csv) allows users to configure project information, [Schematic options](https://sage-schematic.readthedocs.io/en/develop/cli_reference.html), aesthetics. The fields are:

- `project_name` - name of DCC in dropdown menu
- `synapse_asset_view` - synapse ID of asset view.
- `data_model_url` - data model URL (**RAW** github file).
- `template_menu_config_file` - path to DCA template dropdown file in repo.
- `logo_location` - path to logo file in repo. Optional.
- `logo_link` - link to DCC website. Optional.
- `manifest_output_format` - `excel` or `google_sheets`. [Schemtic manifest get option](https://sage-schematic.readthedocs.io/en/develop/cli_reference.html#schematic-manifest-get).
- `manifest_use_annotations` - `TRUE` or `FALSE`. [Schemtic manifest get option](https://sage-schematic.readthedocs.io/en/develop/cli_reference.html#schematic-manifest-get).
- `validate_restrict_rules` - `TRUE` or `FALSE`. [Schematic model validate and submit option](https://sage-schematic.readthedocs.io/en/develop/cli_reference.html#schematic-model-validate).
- `submit_use_schema_labels` - `TRUE` or `FALSE`. [Schematic model submit option](https://sage-schematic.readthedocs.io/en/develop/cli_reference.html#schematic-model-submit).
- `submit_table_manipulation` - `replace` or `upsert`. [Schematic model submit option](https://sage-schematic.readthedocs.io/en/develop/cli_reference.html#schematic-model-submit).
- `submit_manifest_record_type` - One of `table_and_file`, `file_only` , `file_and_entities` or `table_file_and_entities`. [Schematic model submit option](https://sage-schematic.readthedocs.io/en/develop/cli_reference.html#schematic-model-submit).
- `submit_hide_blanks` - `TRUE` or `FALSE`. [Schematic model submit option](https://sage-schematic.readthedocs.io/en/develop/cli_reference.html#schematic-model-submit).
- `submit_upload_file_annotations` - `TRUE` or `FALSE`.
- `use_compliance_dashboard` - `TRUE` or `FALSE`. Only FALSE currently supported. Data compliance dashboard.
- `primary_col` - center header color hex code. Optional.
- `secondary_col` - right header color hex code. Optional.
- `sidebar_col` - left header color hex code. Optional.
