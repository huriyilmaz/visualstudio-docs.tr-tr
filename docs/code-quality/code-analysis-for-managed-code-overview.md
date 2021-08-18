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
ms.openlocfilehash: 5fbd9e0df806e038e4016a128a4340aa46777470
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031737"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visual Studio'de .NET için kod analizine genel Visual Studio

Visual Studio, yönetilen kodun kod analizini iki şekilde gerçekleştirebilir: Eski analiz ile [,](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)yönetilen derlemelerin FxCop statik analizi olarak da bilinir ve daha modern .NET Compiler Platform tabanlı kod [çözümleyicileri](../code-quality/roslyn-analyzers-overview.md)ile. .NET Compiler Platform kodunuzu siz yazarak canlı olarak analiz eden ve yalnızca derlenmiş kodu analiz eden eski FxCop statik kod analizinin yerini alan kod çözümleyicileridir.
