---
lab:
  title: 將模型定型
ms.openlocfilehash: dffa9edda34c599dfbd372fe898ddcf955f6f200
ms.sourcegitcommit: 66d8872bc3d24c2121e225be132b56f4df7920ac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2022
ms.locfileid: "145195728"
---
# <a name="train-models"></a>將模型定型

機器學習的重點在於定型模型，為應用程式提供預測服務。 在此練習中，您將瞭解如何使用 Azure Machine Learning 實驗來執行定型指令碼，以及如何註冊所產生的定型模型。

## <a name="before-you-start"></a>開始之前

若您尚未這樣做，請完成 *[建立 Azure Machine Learning 工作區](01-create-a-workspace.md)* 練習，以建立 Azure Machine Learning 工作區與計算執行個體，並複製本練習所需的筆記本。

## <a name="open-jupyter"></a>開啟 Jupyter

雖然您可以使用 Azure Machine Learning 工作室中的 [Notebooks] 頁面來執行筆記本，但若是能使用 *Jupyter* 等功能更完整的筆記本開發環境，通常能提供較高的生產力。

1. 在 [Azure Machine Learning 工作室](https://ml.azure.com)中，檢視工作區的 [計算] 頁面，如果計算執行個體尚未執行，請在 [計算執行個體] 索引標籤中啟動計算執行個體。
2. 在執行個體順利執行後，請按一下 [Jupyter] 連結，以在瀏覽器的新索引標籤中開啟 Jupyter 首頁。

> **秘訣**：Python 的新手嗎？ 使用 [Python 速查表](cheat-sheets/dp100-cheat-sheet-python.pdf)來瞭解程式碼。 機器學習的新手嗎？ 簡易使用[機器學習概觀](cheat-sheets/dp100-cheat-sheet-machine-learning.pdf)來取得 Azure Machine Learning 中機器學習流程的簡略概觀。

## <a name="train-models-using-the-azure-machine-learning-sdk"></a>使用 Azure Machine Learning SDK 將模型定型

在此練習中，讓模型定型的程式碼會提供在筆記本中。

1. 在 Jupyter 首頁上，流覽至您複製筆記本存放庫的 **/users/*您的使用者名稱*/mslearn-dp100** 資料夾，然後開啟 [將模型定型] 筆記本。
2. 然後讀取筆記本中的筆記，接著依序執行每個程式碼儲存格。
3. 在筆記本中完成執行程式碼後，在 [檔案] 功能表上，按一下 [關閉並停止] 將其關閉，並關閉其 Python 核心。 然後關閉所有的 Jupyter 瀏覽器索引標籤。

## <a name="clean-up"></a>清除

如果您已完成在 Azure Machine Learning 上的作業，請在 Azure Machine Learning 工作室 [計算] 頁面的 [計算執行個體] 索引標籤上選取計算執行個體，然後按一下 [停止] 以將其關閉。 或者您也能讓它繼續運行，以進行下個實驗室練習。

> **注意**：停止您的計算可確保您的訂用帳戶不需支付計算資源的費用。 不過，只要您的訂用帳戶中有 Azure Machine Learning 工作區，您就必須為了資料儲存空間支付少量的費用。 如果您已完成探索 Azure Machine Learning，則可刪除包含 Azure Machine Learning 工作區及其相關的資源群組。 不過，如果您打算完成此系列的任何其他實驗室，則必須重複 *[建立 Azure Machine Learning 工作區](01-create-a-workspace.md)* 練習，以先建立工作區並準備好環境。