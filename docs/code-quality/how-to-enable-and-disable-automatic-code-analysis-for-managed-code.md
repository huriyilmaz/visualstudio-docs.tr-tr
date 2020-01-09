---
title: Eski Kod analizini devre dışı bırak
ms.date: 10/04/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 42d981505817a4de72ed60b896742d4551ca0ee4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587504"
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
