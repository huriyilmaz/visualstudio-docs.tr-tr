---
title: Yönetilen kod için kod analizi
ms.date: 08/27/2020
description: Visual Studio .NET Compiler Platform tabanlı kod çözümleyicileri hakkında bilgi edinin. Bu çözümleyiciler neden yönetilen derlemelerin FxCop statik analizini değiştirmesini anlayın.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 5fbd9e0df806e038e4016a128a4340aa46777470
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632085"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visual Studio .NET için kod çözümlemesine genel bakış

Visual Studio yönetilen kodun kod analizini iki şekilde gerçekleştirebilir: [eski analizler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), yönetilen derlemelerin FxCop statik analizini ve daha modern [.NET Compiler Platform tabanlı kod çözümleyicileri](../code-quality/roslyn-analyzers-overview.md)olarak da bilinir. kodunuzu yazarken canlı olarak çözümleyen .NET Compiler Platform tabanlı kod çözümleyicileri, yalnızca derlenen kodu çözümleyen eski FxCop statik kod analizini değiştirir.
