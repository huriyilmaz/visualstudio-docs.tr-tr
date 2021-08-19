---
title: Eski kod analizini devre dışı bırakma
ms.date: 10/04/2019
description: İkili kod analizini nasıl aç ve kapat? Visual Studio. Yönetilen kod projelerinde bu özelliği yapılandırmaya bakın.
ms.custom: SEO-VS-2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: c687a8c2fd1293913670af4489dfb5c9663344c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147355"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Nasıllı: Yönetilen kod için ikili kod analizini etkinleştirme ve devre dışı bırakma

Yönetilen kod projesinin her derlemesinde çalıştırılan eski kod analizini (ikili analiz) yapılandırabilirsiniz. Ayrıca, her derleme yapılandırması için hata ayıklama ve sürüm gibi farklı ayarlarınız da olabilir.

> [!NOTE]
> Eski analiz, .NET Core ve diğer uygulamalar gibi daha yeni proje .NET Standard kullanılamaz. Bu projeler, [.NET Compiler Platform hem de derleme zamanında](roslyn-analyzers-overview.md) analiz etmek için .NET Compiler Platform tabanlı kod çözümleyicileri kullanır. Bu projelerde kaynak kodu analizini devre dışı bırakma hakkında bilgi için bkz. Kaynak kodu [analizini devre dışı bırakma.](disable-code-analysis.md)

Eski kod analizini etkinleştirmek veya devre dışı bırakmak için:

1. Bu **Çözüm Gezgini** projesini seçin, basılı tutun (veya sağ tıklayın) ve ardından Özellikler'i **seçin.**

2. Projenin özellikler iletişim kutusunda Code Analysis **sekmesine** gidin.

3. Yapılandırma'da derleme **türünü ve** Platform'da hedef platformu **belirtin.** (Non-.NET Core/.NET Standard projeleri.)

::: moniker range="vs-2017"

4. Otomatik kod analizini etkinleştirmek veya devre dışı bırakmak için Derlemede Code Analysis **etkinleştir onay kutusunu** seçin veya temizleyin.

::: moniker-end

::: moniker range=">=vs-2019"

4. Otomatik kod analizini etkinleştirmek veya devre  dışı bırakmak için İkili çözümleyiciler bölümünde Derlemede çalıştır onay kutusunu seçin **veya temizleyin.**

   ![Derlemede ikili kod analizi çalıştırma seçeneği Visual Studio](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> Derlemede ikili kod analizinin devre dışı [bırakılması, .NET Compiler Platform](roslyn-analyzers-overview.md)tabanlı kod çözümleyicilerini etkilemez. Bunları bir derleme paketi olarak yüklemiş olursanız her zaman derlemede NuGet yürütün. Bu çözümleyicilerden analizi devre dışı bırakma hakkında bilgi için bkz. Kaynak kodu [analizini devre dışı bırakma.](disable-code-analysis.md)
