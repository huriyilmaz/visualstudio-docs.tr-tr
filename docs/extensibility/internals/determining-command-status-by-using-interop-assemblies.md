---
title: Birlikte Çalışma Derlemelerini Kullanarak Komut Durumunu | Microsoft Docs
description: Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget arabirimini kullanarak VSPackage'da işilen komutların durumunu belirlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ba74c731fd0d4c531383ae4054fcfe5911b929dc24a27bd644b267cbce0a606c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359578"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Birlikte çalışma derlemelerini kullanarak komut durumunu belirleme
VSPackage' ın işleyebiliyor olduğu komutların durumunu izlemesi gerekir. Ortam, VSPackage içinde etkinleştirilmiş bir komutun ne zaman etkin veya devre dışı bırakılacaklarını belirleye değildir. Ortamı komut durumları hakkında bilgilendirmek VSPackage'nizin sorumluluğundadır; örneğin, **Kes,** Kopyala ve Yapıştır gibi genel komutların **durumu.**

## <a name="status-notification-sources"></a>Durum bildirimi kaynakları
 Ortam, VSPackage'ın arabirimi uygulamasının bir parçası olan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackages yöntemi aracılığıyla komutlar hakkında bilgi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> alır. Ortam, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage'ın yöntemini iki koşullar altında çağırmaktadır:

- Kullanıcı bir ana menü veya bağlam menüsü açtığında (sağ tıklayarak), ortam bu menüyü tüm komutlarda yöntemini yürüterek durumunu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> belirler.

- VSPackage, ortamın geçerli kullanıcı arabirimini (UI) güncelleştirmesini talep eder. Bu güncelleştirme, standart araç çubuğundaki **Kes,** Kopyala **ve** Yapıştır gruplama gibi kullanıcıya görünür olan komutlar olarak gerçekleşir, bağlam ve kullanıcı eylemlerine yanıt olarak etkin ve devre dışı bırakılır. 

  Kabuk birden çok VSPackage barındırır, komut durumunu belirlemek için her VSPackage'ın yoklaması gerektiğinde kabuğun performansı kabul edilemez bir şekilde düşebilir. Bunun yerine, VSPackage'nız değişiklik zamanında kullanıcı arabirimi değiştiklerinde ortamı etkin bir şekilde bilgilendirmesi gerekir. Güncelleştirme bildirimi hakkında daha fazla bilgi için [bkz. Kullanıcı arabirimini güncelleştirme.](../../extensibility/updating-the-user-interface.md)

## <a name="status-notification-failure"></a>Durum bildirimi hatası
 VSPackage'nizin bir komut durumu değişikliğini ortama bildirme hatası, kullanıcı arabirimini tutarsız bir durumda yer alıyor olabilir. Menü veya bağlam menüsü komutlarının kullanıcı tarafından bir araç çubuğuna yerleştirilebiliyor olduğunu unutmayın. Bu nedenle, kullanıcı arabirimini yalnızca bir menü veya bağlam menüsü açıldığında güncelleştirmek yeterli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Uygulama](../../extensibility/internals/command-implementation.md)
