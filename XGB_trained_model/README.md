# Trained XGBoost model for CO2 uptake prediction

This package contains the trained model used by the authors' deployed
MOF-CO2-XPredict system. It is provided for model inspection and inference.

## Included files

- `co2_xgb_model.ubj`: trained XGBoost Booster in UBJ format.
- `model_metadata.json`: required feature order, categorical encodings, model
  hyperparameters, training ranges, sample count, and performance metrics.
- `requirements.txt`: minimal software dependencies.
- `SHA256SUMS.txt`: model integrity checksum.

## Loading the model

The model can be loaded using XGBoost 2.1.4:

```python
import xgboost as xgb

model = xgb.Booster()
model.load_model("co2_xgb_model.ubj")
```

Inputs must follow the exact order in `model_metadata.json` under
`feature_cols`. Categorical values must be converted using the mappings under
`category_codes` before prediction.

## Model summary

- Target: CO2 uptake (mmol/g)
- Training records: 275
- Input features: 18
- Train R2: 0.9995602894
- Test R2: 0.9659498040
- Test RMSE: 0.4255801454 mmol/g
- Test MAE: 0.3004732992 mmol/g

The authors' full training code, application source code, user-interface code,
original notebook, and training dataset are not included in this package.
