---
lab:
  title: 建立 Azure Machine Learning 工作區
ms.openlocfilehash: c2f33973281221da1a4871f19fbaff8f127d028f
ms.sourcegitcommit: 8601551af6c32a4c75fd9ecffce750583c2ab4b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2022
ms.locfileid: "145195749"
---
# <a name="create-and-explore-an-azure-machine-learning-workspace"></a>建立並探索 Azure Machine Learning 工作區

在此練習中，您將建立並探索 Azure Machine Learning 工作區。

## <a name="create-an-azure-machine-learning-workspace"></a>建立 Azure Machine Learning 工作區

顧名思義，工作區是一個可讓您集中管理機器學習專案所需的所有 Azure ML 資產的地方。

1. 在 [Azure 入口網站](https://portal.azure.com)中，以下列指定的設定新建一個 **Azure Machine Learning** 資源：

    - **訂用帳戶**：Azure 訂閱
    - **資源群組**：*建立或選取資源群組*
    - **工作區名稱**：*輸入工作區的唯一名稱*
    - **區域**：*選取最接近您所在位置的地理區域*
    - **儲存體帳戶**：*指定將為您的工作區建立的預設新儲存體帳戶*
    - **金鑰保存庫**：*指定將為您的工作區建立的預設新金鑰保存庫*
    - **Application Insights**：*指定將為您的工作區建立的預設新應用程式見解資源*
    - **容器登錄**：無 (*第一次將模型部署到容器時會自動建立*)

    > **注意**：在建立 Azure Machine Learning 工作區後，您可以使用一些進階選項來限制透過 *私人端點* 的存取，並指定資料加密的自訂金鑰。 我們不會在此練習中使用這些選項，但請您記得並留意這些選項！

2. 在建立好工作區及與其相關聯的資源後，請在入口網站中檢視工作區。

## <a name="explore-azure-machine-learning-studio"></a>探索 Azure Machine Learning 工作室

您可以在 Azure 入口網站中管理某些工作區資產，但對於資料科學家而言，此工具中包含了許多與管理一般 Azure 資源時並無關聯的資訊和連結。 *Azure Machine Learning 工作室* 提供了專用的入口網站來處理您的工作區。

1. 在 Azure Machine Learning 工作區的 [Azure 入口網站] 刀鋒視窗中，按一下要啟動工作室的連結；或者在新瀏覽器索引標籤中，開啟 [https://ml.azure.com](https://ml.azure.com)。 如果出現提示，請使用您在上一個工作中所使用的 Microsoft 帳戶登入，然後選取您的 Azure 訂閱和工作區。

    > **提示** 如果您有多個 Azure 訂閱，您必須先選擇定義了該訂閱的 Azure *目錄*；然後選擇訂閱，最後再選擇工作區。

2. 檢視工作區的 Azure Machine Learning 工作室介面 - 您可以從這裡管理工作區中的所有資產。
3. 在 Azure Machine Learning 工作室中，切換左上方的 &#9776; 圖示，以顯示與隱藏介面中的各種頁面。 您可以使用這些頁面管理工作區中的資源。

## <a name="create-a-compute-instance"></a>建立計算執行個體

Azure Machine Learning 的其中一個優點是能夠建立雲端式計算，讓您能大規模執行實驗和定型指令碼。

1. 在 Azure Machine Learning 工作室中檢視 [計算] 頁面。 您能在此管理資料科學活動的計算資源。 您可建立四種計算資源：
    - **計算執行個體**：資料科學家可用來處理資料與模型的開發工作站。
    - **計算叢集**：可調整的虛擬機器叢集，可視需要處理實驗程式碼。
    - **推斷叢集**：預測性服務的部署目標，而這些預測性服務會使用已定型的模型。
    - **連結的計算**：其他 Azure 計算資源 (例如虛擬機器或 Azure Databricks 叢集) 的連結。

    在此練習中，您將建立計算執行個體，以便在工作區中執行一些程式碼。

2. 在 [計算執行個體] 索引標籤上，使用下列設定新增新的計算執行個體。 您將使用此做為工作站，藉此在筆記本中執行程式碼。
    - **計算名稱**：輸入唯一的名稱
    - **位置**：*與您的工作區服務位置相同*
    - **虚拟机类型**：CPU
    - **虛擬機器大小**：Standard_DS11_v2
    - **總共可用配額**：此會顯示可用的專用核心。
    - **顯示進階設定**：請注意下列的設定，但不要選取它們： 
        - **啟用 SSH 存取**：已取消選取 *(您能使用此選項來啟用利用 SSH 用戶端來對虛擬機器進行直接存取)*
        - **啟用虛擬網路**：已取消選取 *(通常會在企業環境下使用此選項來增強網路安全性)*
        - **指派給另一位使用者**：已取消選取 *(您能使用此選項來將計算執行個體指派給資料科學家)* 3.等待計算執行個體啟動且其狀態改變至 [執行中]。

> **注意**：計算執行個體和叢集是以標準 Azure 虛擬機器映像為基礎。 針對此練習，建議使用 *Standard_DS11_v2* 映像，以達到最佳的成本與效能平衡。 如果您的訂用帳戶具有不包含此映像的配額，請選擇替代映像；但請記得，較大的映像可能會產生較高的成本，而較小的映像可能不足以完成工作。 或者，請要求您的 Azure 系統管理員擴大您的配額。

## <a name="clone-and-run-a-notebook"></a>複製並執行筆記本

許多資料科學和機器學習實驗都是藉由在 *筆記本* 中執行程式碼來執行。 您的計算執行個體中包含了功能完整的 Python 筆記本環境 (*Jupyter* 和 *JuypyterLab*)，可供您用於廣泛的工作；但若要進行基本的筆記本編輯作業，您可以使用 Azure Machine Learning 工作室中內建的 [筆記本] 頁面。

1. 在 Azure Machine Learning 工作室中，檢視 [筆記本] 頁面。
2. 如果有描述新功能的訊息彈出，請關閉。
3. 選取 [終端] 或 [開啟終端] 圖示以開啟終端，並確定其 [計算] 已設定為計算執行個體，且目前的路徑是 **/users/您的使用者名稱** 資料夾。
4. 輸入下列命令，將包含筆記本、資料和其他檔案的 Git 存放庫複製到您的工作區：

    ```bash
    git clone https://github.com/MicrosoftLearning/mslearn-dp100 mslearn-dp100
    ```

4. 在命令完成後，按一下 [檔案] 窗格中的 [&#8635;] 以重新整理檢視，並確認已建立新的 **/users/*您的使用者名稱*/mslearn-dp100** 資料夾。 此資料夾中包含了多個 **.ipynb** Notebook 檔案。
5. 關閉終端窗格，結束會話。
6. 在 **/users/*您的使用者名稱*/mslearn-dp100** 資料夾中，開啟 **開始使用 Notebooks** 筆記本。 然後閱讀筆記，並遵循當中所包含的指示。

> **秘訣**：若要執行程式碼儲存格，請選取您要執行的儲存格，然後使用 [&#9655;] 按鈕來執行它。 

> **Python 的新手嗎？** 使用 [Python 速查表](cheat-sheets/dp100-cheat-sheet-python.pdf)來瞭解程式碼。

> **機器學習的新手嗎？** 使用[機器學習概觀](cheat-sheets/dp100-cheat-sheet-machine-learning.pdf)來取得 Azure Machine Learning 中機器學習流程的簡略概觀。

## <a name="stop-your-compute-instance"></a>停止計算執行個體

如果您目前已完成探索 Azure Machine Learning，您應該關閉計算執行個體，以避免在 Azure 訂閱中產生不必要的費用。

1. 在 Azure Machine Learning 工作室的 [計算] 頁面上，選取您的計算執行個體。
2. 按一下 [停止] 以停止計算執行個體。 當關閉時，其狀態會變更為 [已停止]。

> **注意**：停止您的計算可確保您的訂用帳戶不需支付計算資源的費用。 不過，只要您的訂用帳戶中有 Azure Machine Learning 工作區，您就必須為了資料儲存空間支付少量的費用。 如果您已完成探索 Azure Machine Learning，則可刪除包含 Azure Machine Learning 工作區及其相關的資源群組。 不過，如果您之後打算完成此系列的任何其他實驗室，則必須重複進行此實驗室，以先建立工作區並準備環境。
