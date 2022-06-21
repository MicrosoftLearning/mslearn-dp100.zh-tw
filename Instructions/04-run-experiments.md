---
lab:
  title: 執行實驗
ms.openlocfilehash: 62b6b79c99142d4311c2d9c0db4b02cfd710feb6
ms.sourcegitcommit: 66d8872bc3d24c2121e225be132b56f4df7920ac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2022
ms.locfileid: "145195742"
---
# <a name="run-experiments"></a>執行實驗

實驗是資料科學家工作的核心。 在 Azure Machine Learning 中，*實驗* 可用來執行指令碼或管線，而且通常可以產生輸出和記錄計量。 在此練習中，您將使用 Azure Machine Learning SDK 將 Python 程式碼作為實驗來執行。

## <a name="before-you-start"></a>開始之前

若您尚未這樣做，請完成 *[建立 Azure Machine Learning 工作區](01-create-a-workspace.md)* 練習，以建立 Azure Machine Learning 工作區與計算執行個體，並複製本練習所需的筆記本。

## <a name="open-jupyter"></a>開啟 Jupyter

雖然您可以使用 Azure Machine Learning 工作室中的 [Notebooks] 頁面來執行筆記本，但若是能使用 *Jupyter* 等功能更完整的筆記本開發環境，通常能提供較高的生產力。 幸運的是，您的 Azure Machine Learning 計算執行個體中包含 Jupyter 的安裝。

> **秘訣**：Jupyter Notebook 是資料科學的常用開放原始碼工具。 如果您不熟悉，可以參考[文件](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html)。

1. 在 [Azure Machine Learning 工作室](https://ml.azure.com)中，檢視工作區的 [計算] 頁面，如果計算執行個體尚未執行，請在 [計算執行個體] 索引標籤中啟動計算執行個體。
2. 在執行個體順利執行後，請按一下 [Jupyter] 連結，以在瀏覽器的新索引標籤中開啟 Jupyter 首頁。請確定開啟的是 *Jupyter* 而非 *JupyterLab*。

> **秘訣**：Python 的新手嗎？ 使用 [Python 速查表](cheat-sheets/dp100-cheat-sheet-python.pdf)來瞭解程式碼。

## <a name="verify-the-azure-machine-learning-sdk-is-installed"></a>確認已安裝 Azure Machine Learning SDK

Azure Machine Learning SDK 預設會安裝在您的計算執行個體上。 請遵循下列步驟來確認安裝。

1. 在 Jupyter Notebook 環境中建立新的 **終端機**。 這會透過命令介面開啟一個新索引標籤。
2. 輸入下列命令以確認是否已安裝 Azure ML SDK：

    ```bash
    pip show azureml-sdk
    ```

    請注意已安裝的 SDK 套件版本。

3. **azureml-sdk** SDK 套件提供與 Azure Machine Learning 搭配使用所需最重要的程式庫。不過，除了主要 SDK 套件之外，還有其他包含實用程式庫的套件。 使用下列命令，來確認包含用以在筆記本中顯示 Azure Machine Learning 資訊之程式庫的 **azureml-widgets** 套件已安裝完成：

    ```bash
    pip show azureml-widgets
    ```

4. 關閉 [終端機] 索引標籤，並返回包含 Jupyter 首頁的索引標籤。

> **詳細資訊**：如需關於安裝 Azure ML SDK 與其選用元件的詳細資訊，請參見 [Azure ML SDK 文件](https://docs.microsoft.com/python/api/overview/azure/ml/install?view=azure-ml-py)。

## <a name="run-experiments-in-a-notebook"></a>在筆記本中執行實驗

Azure Machine Learning 中的實驗必須從某種 *控制* 層起始，通常是指令碼或程式。 在此練習中，您將使用筆記本來控制實驗。

1. 在 Jupyter 首頁上，流覽至您複製筆記本存放庫的 **/users/*您的使用者名稱*/mslearn-dp100** 資料夾，然後開啟 [執行實驗] 筆記本。
2. 然後讀取筆記本中的筆記，接著依序執行每個程式碼儲存格。
3. 在筆記本中完成執行程式碼後，在 [檔案] 功能表上，按一下 [關閉並停止] 將其關閉，並關閉其 Python 核心。 然後關閉所有的 Jupyter 瀏覽器索引標籤。

## <a name="clean-up"></a>清除

如果您已完成在 Azure Machine Learning 上的作業，請在 Azure Machine Learning 工作室 [計算] 頁面的 [計算執行個體] 索引標籤上選取計算執行個體，然後按一下 [停止] 以將其關閉。 或者您也能讓它繼續執行，以進行下個實驗室練習。

> **注意**：停止您的計算可確保您的訂用帳戶不需支付計算資源的費用。 不過，只要您的訂用帳戶中有 Azure Machine Learning 工作區，您就必須為了資料儲存空間支付少量的費用。 如果您已完成探索 Azure Machine Learning，則可刪除包含 Azure Machine Learning 工作區及其相關的資源群組。 不過，如果您打算完成此系列的任何其他實驗室，則必須重複 *[建立 Azure Machine Learning 工作區](01-create-a-workspace.md)* 練習，以先建立工作區並準備好環境。