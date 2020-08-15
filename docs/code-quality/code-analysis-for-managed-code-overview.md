---
title: Yönetilen kod için kod analizi
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 901c66a97a763345ee32b1a1540a7998934d0ff3
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248985"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Visual Studio 'da yönetilen kod için kod çözümlemesine genel bakış

Visual Studio yönetilen kodun Kod analizini iki şekilde gerçekleştirebilir: yönetilen derlemelerin FxCop statik analizini ve daha modern [.net Compiler platform tabanlı kod Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md)olarak da bilinen [eski analizler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md). Kodunuzu yazarken canlı olarak çözümleyen .NET Compiler Platform tabanlı kod Çözümleyicileri, yalnızca derlenen kodu çözümleyen eski FxCop statik Kod analizini değiştirir.
