---
title: 線上託管說明
permalink: index.html
layout: home
ms.openlocfilehash: a2eb157b1d188655f4cfbcc575befec4a2e9c623
ms.sourcegitcommit: 18f734eeb1031a9cb69c3b294632efd2e69324ac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2021
ms.locfileid: "145195748"
---
# <a name="azure-machine-learning-exercises"></a>Azure Machine Learning 練習

此存放庫包含適用於 Microsoft 課程的實作教室練習 [DP-100 *在 Azure 上設計及實作資料科學解決方案*](https://docs.microsoft.com/learn/certifications/courses/dp-100t01)和 [Microsoft Learn 上等效的自學型課程模組](https://docs.microsoft.com/learn/paths/build-ai-solutions-with-azure-ml-service/)。 此練習是為了配合學習材料並讓您使用其描述的技術進行練習而設計。

您將會需要 Microsoft Azure 訂閱，以完成這些練習。 若您的講師沒有為您提供 Microsoft Azure 訂閱，您可以在 [https://azure.microsoft.com](https://azure.microsoft.com) 註冊免費試用版。

{% assign labs = site.pages | where_exp:"page", "page.url contains '/instructions'" %}
| Exercises |
| ------- | 
{% for activity in labs  %}| [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
