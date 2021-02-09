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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 542747f650888b384a9f9c4910b0d9caea93e948
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860574"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visual Studio 'da .NET için kod çözümlemesine genel bakış

Visual Studio yönetilen kodun Kod analizini iki şekilde gerçekleştirebilir: yönetilen derlemelerin FxCop statik analizini ve daha modern [.net Compiler platform tabanlı kod Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md)olarak da bilinen [eski analizler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md). Kodunuzu yazarken canlı olarak çözümleyen .NET Compiler Platform tabanlı kod Çözümleyicileri, yalnızca derlenen kodu çözümleyen eski FxCop statik Kod analizini değiştirir.
