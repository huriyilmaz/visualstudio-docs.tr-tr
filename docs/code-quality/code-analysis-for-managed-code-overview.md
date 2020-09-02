---
title: Yönetilen kod için kod analizi
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d13a8afdfcbeb6ae9f91e39779af8b82b2461000
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89091414"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visual Studio 'da .NET için kod çözümlemesine genel bakış

Visual Studio yönetilen kodun Kod analizini iki şekilde gerçekleştirebilir: yönetilen derlemelerin FxCop statik analizini ve daha modern [.net Compiler platform tabanlı kod Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md)olarak da bilinen [eski analizler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md). Kodunuzu yazarken canlı olarak çözümleyen .NET Compiler Platform tabanlı kod Çözümleyicileri, yalnızca derlenen kodu çözümleyen eski FxCop statik Kod analizini değiştirir.
