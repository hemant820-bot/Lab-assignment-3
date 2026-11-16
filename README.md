# Lab-assignment-3
{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": []
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "code",
      "execution_count": 1,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 538
        },
        "id": "fbOcX_EbAwr-",
        "outputId": "a234d350-2a01-44d6-8c5f-d9723c02da61"
      },
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "First 5 rows of the dataset:\n"
          ]
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "   record_id  failed_logins  login_hour  new_device  data_transfer_mb  label\n",
              "0          1              4           1           0             164.9      1\n",
              "1          2              3           3           1             250.6      1\n",
              "2          3              3          10           0             145.1      0\n",
              "3          4              2          11           0             397.8      0\n",
              "4          5              1           3           0             409.3      0"
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-86e29ffe-ee3f-4183-b468-759d4cfae9db\" class=\"colab-df-container\">\n",
              "    <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>record_id</th>\n",
              "      <th>failed_logins</th>\n",
              "      <th>login_hour</th>\n",
              "      <th>new_device</th>\n",
              "      <th>data_transfer_mb</th>\n",
              "      <th>label</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>1</td>\n",
              "      <td>4</td>\n",
              "      <td>1</td>\n",
              "      <td>0</td>\n",
              "      <td>164.9</td>\n",
              "      <td>1</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>2</td>\n",
              "      <td>3</td>\n",
              "      <td>3</td>\n",
              "      <td>1</td>\n",
              "      <td>250.6</td>\n",
              "      <td>1</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>3</td>\n",
              "      <td>3</td>\n",
              "      <td>10</td>\n",
              "      <td>0</td>\n",
              "      <td>145.1</td>\n",
              "      <td>0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>4</td>\n",
              "      <td>2</td>\n",
              "      <td>11</td>\n",
              "      <td>0</td>\n",
              "      <td>397.8</td>\n",
              "      <td>0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>5</td>\n",
              "      <td>1</td>\n",
              "      <td>3</td>\n",
              "      <td>0</td>\n",
              "      <td>409.3</td>\n",
              "      <td>0</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-86e29ffe-ee3f-4183-b468-759d4cfae9db')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-86e29ffe-ee3f-4183-b468-759d4cfae9db button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-86e29ffe-ee3f-4183-b468-759d4cfae9db');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "    </div>\n",
              "  </div>\n"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "dataframe",
              "summary": "{\n  \"name\": \"print(\\\"\\\\nDataset Shape:\\\", df\",\n  \"rows\": 5,\n  \"fields\": [\n    {\n      \"column\": \"record_id\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 1,\n        \"min\": 1,\n        \"max\": 5,\n        \"num_unique_values\": 5,\n        \"samples\": [\n          2,\n          5,\n          3\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"failed_logins\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 1,\n        \"min\": 1,\n        \"max\": 4,\n        \"num_unique_values\": 4,\n        \"samples\": [\n          3,\n          1,\n          4\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"login_hour\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 4,\n        \"min\": 1,\n        \"max\": 11,\n        \"num_unique_values\": 4,\n        \"samples\": [\n          3,\n          11,\n          1\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"new_device\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 0,\n        \"max\": 1,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          1,\n          0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"data_transfer_mb\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 125.19689692640151,\n        \"min\": 145.1,\n        \"max\": 409.3,\n        \"num_unique_values\": 5,\n        \"samples\": [\n          250.6,\n          409.3\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"label\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0,\n        \"min\": 0,\n        \"max\": 1,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          0,\n          1\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}"
            }
          },
          "metadata": {}
        },
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "\n",
            "Dataset Information:\n",
            "<class 'pandas.core.frame.DataFrame'>\n",
            "RangeIndex: 100 entries, 0 to 99\n",
            "Data columns (total 6 columns):\n",
            " #   Column            Non-Null Count  Dtype  \n",
            "---  ------            --------------  -----  \n",
            " 0   record_id         100 non-null    int64  \n",
            " 1   failed_logins     100 non-null    int64  \n",
            " 2   login_hour        100 non-null    int64  \n",
            " 3   new_device        100 non-null    int64  \n",
            " 4   data_transfer_mb  100 non-null    float64\n",
            " 5   label             100 non-null    int64  \n",
            "dtypes: float64(1), int64(5)\n",
            "memory usage: 4.8 KB\n",
            "\n",
            "Dataset Shape: (100, 6)\n"
          ]
        }
      ],
      "source": [
        "\n",
        "import numpy as np\n",
        "import pandas as pd\n",
        "import matplotlib.pyplot as plt\n",
        "\n",
        "# Load the dataset\n",
        "df = pd.read_csv('/content/simple_cyber_activity.csv')\n",
        "\n",
        "# Display first 5 rows\n",
        "print(\"First 5 rows of the dataset:\")\n",
        "display(df.head())\n",
        "\n",
        "# Display dataset information\n",
        "print(\"\\nDataset Information:\")\n",
        "df.info()\n",
        "\n",
        "# Check dataset shape\n",
        "print(\"\\nDataset Shape:\", df.shape)\n"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "\n",
        "# Q1. CNN, RNN/LSTM and GAN Concept Matching\n",
        "\n",
        "### AIM\n",
        "To connect three deep-learning models with suitable cybersecurity data and applications.\n",
        "\n",
        "### Concept Matching Table\n",
        "\n",
        "| Model | Suitable Data | Cyber-Security Example |\n",
        "|---|---|---|\n",
        "| CNN | Images / Grid-like data | Malware image classification |\n",
        "| RNN / LSTM | Sequences / Logs / Time series | Sequential intrusion or authentication-log analysis |\n",
        "| GAN | Synthetic-data generation | Generate controlled synthetic attack samples |\n",
        "| Dense Network | Small numeric feature table | Normal/Attack classification |\n",
        "\n",
        "### Why is a Dense Neural Network used in this practical?\n",
        "\n",
        "A Dense Neural Network is used because our dataset contains four numeric input features: failed_logins, login_hour, new_device and data_transfer_mb. It is suitable for learning patterns from this small numerical dataset and classifying activities as Normal or Attack.\n"
      ],
      "metadata": {
        "id": "5AO1JNV-CKdk"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "\n",
        "from sklearn.model_selection import train_test_split\n",
        "from sklearn.preprocessing import StandardScaler\n",
        "\n",
        "# Select input features and output label\n",
        "features = ['failed_logins', 'login_hour', 'new_device', 'data_transfer_mb']\n",
        "\n",
        "X = df[features]\n",
        "y = df['label']\n",
        "\n",
        "# Split dataset (75% training, 25% testing)\n",
        "X_train, X_test, y_train, y_test = train_test_split(\n",
        "    X, y, test_size=0.25, random_state=42, stratify=y\n",
        ")\n",
        "\n",
        "# Normalize data\n",
        "scaler = StandardScaler()\n",
        "X_train_scaled = scaler.fit_transform(X_train)\n",
        "X_test_scaled = scaler.transform(X_test)\n",
        "\n",
        "# Display results\n",
        "print(\"Class Counts:\")\n",
        "print(y.value_counts())\n",
        "\n",
        "print(\"\\nTraining Shape:\", X_train_scaled.shape)\n",
        "print(\"Testing Shape:\", X_test_scaled.shape)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "K82fEOdwCd1l",
        "outputId": "4b733560-897c-41c8-9cd2-5576fd42ff62"
      },
      "execution_count": 2,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Class Counts:\n",
            "label\n",
            "0    75\n",
            "1    25\n",
            "Name: count, dtype: int64\n",
            "\n",
            "Training Shape: (75, 4)\n",
            "Testing Shape: (25, 4)\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "### Normalization\n",
        "StandardScaler converts features into a common scale so that large-valued features do not dominate the model. It is fitted only on training data."
      ],
      "metadata": {
        "id": "sS-6tqMECgZA"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "\n",
        "import tensorflow as tf\n",
        "\n",
        "# Set random seeds\n",
        "np.random.seed(42)\n",
        "tf.random.set_seed(42)\n",
        "\n",
        "# Create 4-8-4-1 Neural Network\n",
        "model = tf.keras.Sequential([\n",
        "    tf.keras.layers.Input(shape=(4,)),\n",
        "    tf.keras.layers.Dense(8, activation='relu'),\n",
        "    tf.keras.layers.Dense(4, activation='relu'),\n",
        "    tf.keras.layers.Dense(1, activation='sigmoid')\n",
        "])\n",
        "\n",
        "# Compile model\n",
        "model.compile(\n",
        "    optimizer='adam',\n",
        "    loss='binary_crossentropy',\n",
        "    metrics=['accuracy']\n",
        ")\n",
        "\n",
        "# Display model architecture\n",
        "model.summary()\n",
        "\n",
        "# Train model\n",
        "history = model.fit(\n",
        "    X_train_scaled,\n",
        "    y_train,\n",
        "    validation_split=0.20,\n",
        "    epochs=20,\n",
        "    batch_size=8,\n",
        "    verbose=1\n",
        ")\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 939
        },
        "id": "jHjVBleZCd4k",
        "outputId": "c97359e8-83a3-4190-81d5-79fa920df1c1"
      },
      "execution_count": 3,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "\u001b[1mModel: \"sequential\"\u001b[0m\n"
            ],
            "text/html": [
              "<pre style=\"white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace\"><span style=\"font-weight: bold\">Model: \"sequential\"</span>\n",
              "</pre>\n"
            ]
          },
          "metadata": {}
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━┓\n",
              "┃\u001b[1m \u001b[0m\u001b[1mLayer (type)                   \u001b[0m\u001b[1m \u001b[0m┃\u001b[1m \u001b[0m\u001b[1mOutput Shape          \u001b[0m\u001b[1m \u001b[0m┃\u001b[1m \u001b[0m\u001b[1m      Param #\u001b[0m\u001b[1m \u001b[0m┃\n",
              "┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━┩\n",
              "│ dense (\u001b[38;5;33mDense\u001b[0m)                   │ (\u001b[38;5;45mNone\u001b[0m, \u001b[38;5;34m8\u001b[0m)              │            \u001b[38;5;34m40\u001b[0m │\n",
              "├─────────────────────────────────┼────────────────────────┼───────────────┤\n",
              "│ dense_1 (\u001b[38;5;33mDense\u001b[0m)                 │ (\u001b[38;5;45mNone\u001b[0m, \u001b[38;5;34m4\u001b[0m)              │            \u001b[38;5;34m36\u001b[0m │\n",
              "├─────────────────────────────────┼────────────────────────┼───────────────┤\n",
              "│ dense_2 (\u001b[38;5;33mDense\u001b[0m)                 │ (\u001b[38;5;45mNone\u001b[0m, \u001b[38;5;34m1\u001b[0m)              │             \u001b[38;5;34m5\u001b[0m │\n",
              "└─────────────────────────────────┴────────────────────────┴───────────────┘\n"
            ],
            "text/html": [
              "<pre style=\"white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace\">┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━┓\n",
              "┃<span style=\"font-weight: bold\"> Layer (type)                    </span>┃<span style=\"font-weight: bold\"> Output Shape           </span>┃<span style=\"font-weight: bold\">       Param # </span>┃\n",
              "┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━┩\n",
              "│ dense (<span style=\"color: #0087ff; text-decoration-color: #0087ff\">Dense</span>)                   │ (<span style=\"color: #00d7ff; text-decoration-color: #00d7ff\">None</span>, <span style=\"color: #00af00; text-decoration-
