

# CPIExtract: Enhanced Extraction of Chemical-Protein Relations

The code presented aims to perform Relation Extraction on the Chemprot dataset. The goal is to identify complex Chemical-Protein interactions, which have various applications in the biomedical domain. We have performed a series of preprocessing tasks catered to specific models and their requirements. Two models were implemented: 
1. An SVM model using Dependency Parsing and ELMO vectorized form.
2. A hybrid model combining CNN, Bi-LSTM, and BioBERT with selective weighted voting.

## Process to Run the Code and Get Results

### Running BioBERT

Execute the following steps to successfully build and run the model:

1. Open a Terminal in the source directory.
2. Create an environment:
    ```sh
    python3 -m venv biobertenv
    ```
3. Activate and use the environment:
    ```sh
    source biobertenv/bin/activate
    ```
4. Install the required libraries:
    ```sh
    pip install -r requirements.txt
    ```
5. To fine-tune the model, run the python file `BioBert_Tuning.py`:
    ```sh
    python BioBert_Tuning.py
    ```
   Note: This process is computationally intensive and time-consuming (approximately 11 hours). Alternatively, you can use the pretrained-tuned model saved under the folders `biobert_tokenizer` and `biobert_finetuned`. The python file also uses `Merged.csv`, which is a combination of Train and Dev datasets included in the zip. If the models come as compressed files, please unzip them before proceeding. The model files can be found [here](https://drive.google.com/drive/folders/1jCzGSbx9dU9Z45Pjkw07zgBZpDj_Caxq).

6. To run the model on the test dataset, execute:
    ```sh
    python Test_BioBert.py
    ```
   This should take around 20 minutes. The output will be saved in a file called `Output.txt`, containing predictions on the test dataset.

### Running CNN and Bi-LSTM

The notebook titled `Voting` covers the creation of the hybrid model. It includes various processes such as importing specific libraries, data preprocessing, and exporting preprocessed data for future use. Note that running the ELMO model is computationally intensive, taking around 30 minutes for Train and 15 minutes for Test data. Therefore, we export the preprocessed data for future use.

The python notebook can be run by opening it in Anaconda Jupyter Notebook or Visual Studio Jupyter Notebooks. The notebook first runs through the preprocessing phase, then runs CNN and Bi-LSTM, and finally reads the output of BioBERT generated in `Output.txt`. These three models are then passed into the Voting process.

**Important**: Ensure that the python notebook is run in the same path as BioBERT since it utilizes the output for voting.

### Running SVM

The notebook titled `SVM` follows a similar template. Simply run the notebook titled `SVM.ipynb` and evaluate the results produced.

**Important**: Ensure that the python notebook is run in the same path as BioBERT and Voting, as it uses the exported Train and Test preprocessed data to reduce time complexity.

---

Feel free to contribute or raise issues if you encounter any problems.
