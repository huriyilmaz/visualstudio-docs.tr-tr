---
title: Yönetilen kod için kod analizi
ms.date: 08/27/2020
description: .NET Compiler Platform tabanlı kod çözümleyicileri hakkında Visual Studio. Bu çözümleyicilerin neden yönetilen derlemelerin FxCop statik analizinin yerini alasınız.
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
ms.openlocfilehash: 08a90f1d2157088f060fe15a5a370413a55b79e7e04e736f7ac0e5a4c9b76e7b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121405610"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visual Studio'de .NET için kod analizine genel bakış

Visual Studio, yönetilen kodun kod analizini iki şekilde gerçekleştirebilir: Eski analiz ile [,](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)yönetilen derlemelerin FxCop statik analizi olarak da bilinir ve daha modern .NET Compiler Platform tabanlı kod [çözümleyicileri](../code-quality/roslyn-analyzers-overview.md)ile. .NET Compiler Platform kodunuzu siz yazarak canlı olarak analiz eden kod çözümleyicileri, yalnızca derlenmiş kodu analiz eden eski FxCop statik kod analizinin yerini almaktadır.
