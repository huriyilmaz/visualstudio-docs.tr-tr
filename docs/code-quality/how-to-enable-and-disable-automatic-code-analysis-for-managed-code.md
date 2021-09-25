---
title: Eski kod analizini devre dışı bırakma
ms.date: 10/04/2019
description: İkili kod analizini açma ve kapatma hakkında bilgi Visual Studio. Yönetilen kod projelerinde bu özelliği yapılandırmaya bakın.
ms.custom: SEO-VS-2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 785ac247f3c1343dc5133cc9d0e3c8c8b4d66a34
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427440"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Nasıllı: Yönetilen kod için ikili kod analizini etkinleştirme ve devre dışı bırakma

Yönetilen kod projesinin her derlemesinde çalıştırılan eski kod analizini (ikili analiz) yapılandırabilirsiniz. Ayrıca, her derleme yapılandırması için hata ayıklama ve sürüm gibi farklı ayarlarınız da olabilir.

> [!NOTE]
> Eski analiz, .NET Core ve diğer uygulamalar gibi daha yeni proje .NET Standard kullanılamaz. Bu projeler hem [.NET Compiler Platform hem de derleme zamanında](roslyn-analyzers-overview.md) kodu analiz etmek için .NET Compiler Platform tabanlı kod çözümleyicileri kullanır. Bu projelerde kaynak kodu analizini devre dışı bırakma hakkında bilgi için bkz. Kaynak kodu [analizini devre dışı bırakma.](disable-code-analysis.md)

Eski kod analizini etkinleştirmek veya devre dışı bırakmak için:

1. Bu **Çözüm Gezgini** projesini seçin, basılı tutun (veya sağ tıklayın) ve ardından Özellikler'i **seçin.**

2. Projenin özellikler iletişim kutusunda Code Analysis **sekmesine** gidin.

3. Yapılandırma'da derleme **türünü ve** Platform'da hedef platformu **belirtin.** (Non-.NET Core/.NET Standard projeleri.)

::: moniker range="vs-2017"

4. Otomatik kod analizini etkinleştirmek veya devre dışı bırakmak için Derlemede Code Analysis **etkinleştir onay kutusunu** işaretleyin veya temizleyin.

::: moniker-end

::: moniker range=">=vs-2019"

4. Otomatik kod analizini etkinleştirmek veya devre  dışı bırakmak için İkili çözümleyiciler bölümünde Derlemede çalıştır onay kutusunu seçin **veya temizleyin.**

   ![Derlemede ikili kod analizi çalıştırma seçeneği Visual Studio](media/run-on-build-binary-analyzers.png)

5. Eski analizi devre dışı bırakmanız gerekirse, proje dosyasında eski kod analizinin devre dışı bırakılmıştır. özelliğini `RunCodeAnalysis` false olarak ayarlayın:

   `<RunCodeAnalysis>false</RunCodeAnalysis>`

::: moniker-end

> [!NOTE]
> Derlemede ikili kod analizinin devre dışı [bırakılması, .NET Compiler Platform](roslyn-analyzers-overview.md)tabanlı kod çözümleyicilerini etkilemez. Bu çözümleyicileri her zaman derleme paketi olarak yüklemiş NuGet yürütün. Bu çözümleyicilerden analizi devre dışı bırakma hakkında bilgi için bkz. Kaynak kodu [analizini devre dışı bırakma.](disable-code-analysis.md)
