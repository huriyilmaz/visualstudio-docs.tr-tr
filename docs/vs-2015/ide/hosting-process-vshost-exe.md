---
title: Barındırma Işlemi (VSHost. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a998246f514f13a575f6a7fef850f9f705f92553
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645540"
---
# <a name="hosting-process-vshostexe"></a>Barındırma Süreci (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Barındırma süreci, Visual Studio 'da hata ayıklama performansını geliştiren, kısmi güven hata ayıklamayı sağlayan ve tasarım zamanı ifade değerlendirmesi sağlayan bir özelliktir. Barındırma işlemi dosyaları dosya adında VSHost içerir ve projenizin çıkış klasörüne yerleştirilir. Daha fazla bilgi için bkz. [hata ayıklama ve barındırma işlemi](../debugger/debugging-and-the-hosting-process.md).

> [!NOTE]
> Barındırma işlem dosyaları (. VSHost. exe), Visual Studio tarafından kullanılır ve doğrudan çalıştırılmamalıdır veya uygulamanızla birlikte dağıtılmalıdır.

## <a name="improved-debugging-performance"></a>Geliştirilmiş hata ayıklama performansı
 Barındırma işlemi bir uygulama etki alanı oluşturur ve hata ayıklayıcıyı uygulamayla ilişkilendirir. Bu görevlerin gerçekleştirilmesi, hata ayıklama işleminin başlatıldığı zaman ve uygulamanın çalışmaya başladığı zaman arasında dikkat çekici bir gecikme ortaya çıkarabilir. Barındırma işlemi, uygulama etki alanını oluşturarak ve hata ayıklayıcıyı arka planda ilişkilendirerek ve uygulama etki alanını ve hata ayıklayıcı durumunu uygulamanın çalıştırmaları arasında kaydederek performansı artırmaya yardımcı olur. Uygulama etki alanları hakkında daha fazla bilgi için bkz. [uygulama etki alanları](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).

## <a name="partial-trust-debugging"></a>Kısmi güven hata ayıklaması
 Uygulama, **Proje Tasarımcısı**'nın [Güvenlik sayfasında](../ide/reference/security-page-project-designer.md) kısmi güven uygulaması olarak belirtilebilir. Kısmi güven uygulamasının hata ayıklaması için uygulama etki alanının özel olarak başlatılması gerekir. Bu başlatma, barındırma işlemi tarafından işlenir.

## <a name="design-time-expression-evaluation"></a>Tasarım zamanı Ifade değerlendirmesi
 Tasarım zamanı ifade değerlendirmesi, uygulamayı çalıştırmak zorunda kalmadan **komut** penceresinden kodu test etmenizi sağlar. Barındırma işlemi, tasarım zamanı ifade değerlendirmesi sırasında bu kodu yürütür. Daha fazla bilgi için bkz. [hemen pencere](../ide/reference/immediate-window.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Hata ayıklama ve barındırma işlemi](../debugger/debugging-and-the-hosting-process.md) [nasıl yapılır: barındırma Işlemini devre dışı bırakma](../ide/how-to-disable-the-hosting-process.md) [penceresi](../ide/reference/immediate-window.md) [uygulama etki alanları](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)
