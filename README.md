# Once
One‑shot ticket primitive on X Layer / TapeOut.

One circuit on one processor.
The ticket arms on ISSUE, fires once on USE, remembers consumption and stays dead until re‑issue.

- Processor: `0xcbc6882ba62a314eeb8a9710a94fd61a5b1a7918`
- Wallet: `0xe13a4ca61a0f3f72709668be265856180f1469c4`
- Circuit tx: https://www.oklink.com/xlayer/tx/0x4a5b9f3b60c325128ae48cee2ed320caa7402d7e8e2c90b6490d0931c1844d61

## Once inputs
- IN0 ISSUE
- IN1 USE
- IN2 REVOKE
- OUT0 ARMED
- OUT1 EXEC

## Once checks

| ISSUE | USE | REVOKE | note | ARMED | EXEC |
|---|---|---|---|---|---|
| 1 | 0 | 0 | Issue ticket, armed ready | 1 | 0 |
| 0 | 1 | 0 | Valid trigger, ticket consumed | 0 | 1 |
| 0 | 1 | 0 | Second USE after consume | 0 | 0 |
| 0 | 0 | 1 | Revoke armed ticket | 0 | 0 |
| 0 | 1 | 0 | USE revoked / empty ticket | 0 | 0 |
