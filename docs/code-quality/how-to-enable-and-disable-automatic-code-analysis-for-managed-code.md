---
title: Eski Kod analizini devre dışı bırak
ms.date: 10/04/2019
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 532fe62ceee3ab32fc203976af58dd867b97b453
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371891"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Nasıl yapılır: yönetilen kod için ikili kod analizini etkinleştirme ve devre dışı bırakma

Bilinen kod analizini (ikili analiz), her bir yönetilen kod projesi derlemeden sonra çalışacak şekilde yapılandırabilirsiniz. Ayrıca, hata ayıklama ve yayın gibi her derleme yapılandırması için farklı ayarlara sahip olabilirsiniz.

> [!NOTE]
> Eski analiz .NET Core ve .NET Standard uygulamaları gibi daha yeni proje türleri için kullanılamaz. Bu projeler, hem canlı hem de derleme zamanında kodu çözümlemek için [.net Compiler platform tabanlı kod Çözümleyicileri](roslyn-analyzers-overview.md) kullanır. Bu projelerde kaynak kodu analizini devre dışı bırakma hakkında daha fazla bilgi için bkz. [kaynak kodu analizini devre dışı bırakma](disable-code-analysis.md).

Eski Kod analizini etkinleştirmek veya devre dışı bırakmak için:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Özellikler**' i seçin.

2. Projenin Özellikler iletişim kutusunda **Kod Analizi** sekmesini seçin.

3. **Yapılandırmada** derleme türünü ve hedef platformu **Platform**' da belirtin. (Yalnızca Non-.NET Core/. NET standart projeler.)

::: moniker range="vs-2017"

4. Otomatik Kod analizini etkinleştirmek veya devre dışı bırakmak için, **derlemede Kod analizini etkinleştir** onay kutusunu işaretleyin veya temizleyin.

::: moniker-end

::: moniker range=">=vs-2019"

4. Otomatik Kod analizini etkinleştirmek veya devre dışı bırakmak için, **ikili çözümleyiciler** bölümünde **derlemeyi Çalıştır** onay kutusunu işaretleyin veya temizleyin.

   ![Visual Studio 'da derleme seçeneğinde ikili kod analizini Çalıştır](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> Derlemede ikili kod analizini devre dışı bırakmak, her zaman derlemede yürütülen [.net Compiler platform tabanlı kod Çözümleyicileri](roslyn-analyzers-overview.md)etkilemez ve bu, bunları bir NuGet paketi olarak yüklediyseniz derleme sırasında yürütülür. Bu çözümleyicilerin analizini devre dışı bırakma hakkında daha fazla bilgi için bkz. [kaynak kodu analizini devre dışı bırakma](disable-code-analysis.md).
