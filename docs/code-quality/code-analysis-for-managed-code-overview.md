---
title: Yönetilen kod için kod analizi
ms.date: 08/27/2020
description: Visual Studio 'da .NET Compiler Platform tabanlı kod Çözümleyicileri hakkında bilgi edinin. Bu çözümleyiciler neden yönetilen derlemelerin FxCop statik analizini değiştirmesini anlayın.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 643e8457dbbe838d593a7bad38064537b6cbe57d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348534"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visual Studio 'da .NET için kod çözümlemesine genel bakış

Visual Studio yönetilen kodun Kod analizini iki şekilde gerçekleştirebilir: yönetilen derlemelerin FxCop statik analizini ve daha modern [.net Compiler platform tabanlı kod Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md)olarak da bilinen [eski analizler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md). Kodunuzu yazarken canlı olarak çözümleyen .NET Compiler Platform tabanlı kod Çözümleyicileri, yalnızca derlenen kodu çözümleyen eski FxCop statik Kod analizini değiştirir.
