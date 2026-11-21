# Statistical analysis scripts

- `raw/wvs_empirical_analysis.py`: script retained from the original-option analysis directory.
- `normalized/wvs_empirical_analysis.py`: script retained from the normalized-score analysis directory.

The two archived scripts currently have identical contents. Each includes both analysis modes and runs both from `main()`. They implement coder agreement, response-distribution distances, interitem association comparisons, item bootstrap intervals, Wilcoxon tests, and figure generation.

## Dependencies and inputs

Use Python 3.10 or later. From the repository root, install the required packages:

```bash
python -m pip install -r analysis/requirements.txt
```

The scripts retain their original input-directory conventions. `ROOT` is the directory containing the script. Each input folder must contain:

```text
4WVS得分数据/                         # Original option codes
├── 真人_WVS结果2-5.xlsx
├── LLM_WVS结果2-5专家1/*.xlsx
├── LLM_WVS结果2-5专家2/*.xlsx
├── 大模型端到端方案/*.xlsx
└── 平均版多智能体/*.xlsx               # Optional supplementary inputs

4WVS得分数据_normalized/              # Normalized workbooks with Q*_norm columns
└── ...                              # Same layout as above
```

The repository's published folders correspond to these original-option inputs as follows:

| Published location | Original input location |
| --- | --- |
| `case190/WVScase190real.xlsx` | `4WVS得分数据/真人_WVS结果2-5.xlsx` |
| `expert1formultiagent/*.xlsx` | `4WVS得分数据/LLM_WVS结果2-5专家1/*.xlsx` |
| `expert2formultiagent/*.xlsx` | `4WVS得分数据/LLM_WVS结果2-5专家2/*.xlsx` |
| `WVSend2end/*.xlsx` | `4WVS得分数据/大模型端到端方案/*.xlsx` |

Prepare the inputs under the script's directory before running it. The normalized input workbooks are separate inputs; they are not supplied by the current repository. Running an archived script directly against an unmodified checkout will therefore require input preparation. Renaming a raw workbook does not normalize its values.

With both input directories prepared, run either archived copy, for example:

```bash
python analysis/raw/wvs_empirical_analysis.py
```

Outputs are written to `eva1/` and `eva1norm/` alongside that script, including statistical tables, figure source data, figures, a report, and an analysis manifest. The scripts do not call language-model APIs.
