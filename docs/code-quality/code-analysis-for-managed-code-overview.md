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
ms.openlocfilehash: e6515c0df7a9c3389e754d5238788d716be49e2e
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800092"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Visual Studio 'da yönetilen kod için kod çözümlemesine genel bakış

Visual Studio, yönetilen kodun Kod analizini iki şekilde gerçekleştirebilir:
- [Eski analizler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)ile yönetilen derlemelerin FxCop statik analizi olarak da bilinir.
- Daha modern [.net Compiler platform tabanlı kod Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md)ile. Kodunuzu yazarken canlı olarak çözümleyen .NET Compiler Platform tabanlı kod Çözümleyicileri, yalnızca derlenen kodu çözümleyen eski FxCop statik Kod analizini değiştirir.