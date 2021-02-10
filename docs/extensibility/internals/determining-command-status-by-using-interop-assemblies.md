---
title: Birlikte çalışma derlemelerini kullanarak komut durumunu belirleme | Microsoft Docs
description: Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget arabirimini kullanarak bir VSPackage içinde işlenen komutların durumunu belirlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5473fffa00723735b022412e7f37f184e043df4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963451"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Birlikte çalışabilirlik derlemelerini kullanarak komut durumunu belirleme
VSPackage, işleyebilmesi için komutların durumunu takip etmelidir. Ortam, VSPackage içinde işlenen bir komutun etkin veya devre dışı olacağını belirleyemiyor. Bu, ortama komut durumları hakkında bilgi vermek için VSPackage 'ın sorumluluğundadır. Örneğin, **Kes**, **Kopyala** ve **Yapıştır** gibi genel komutların durumu.

## <a name="status-notification-sources"></a>Durum bildirim kaynakları
 Ortam, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> arabirim uygulamanın VSPackage 'un bir parçası olan VSPackages ' yöntemi aracılığıyla komutlar hakkında bilgi alır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Ortam, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> iki koşulda VSPackage yöntemini çağırır:

- Bir Kullanıcı ana menüyü veya bağlam menüsünü açtığında (sağ tıklanarak), ortam, durumlarını <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> belirlemede Bu menüdeki tüm komutlarda yöntemini yürütür.

- VSPackage, ortamın geçerli kullanıcı arabirimini (UI) güncelleştirmesini istediğinde. Bu güncelleştirme, Standart araç çubuğunda **kesme**, **kopyalama** ve **Yapıştırma** gruplandırması gibi, kullanıcıya şu anda görünür olan ve bağlam ve kullanıcı eylemlerine yanıt olarak etkin ve devre dışı bırakılmış olan komutlar olarak oluşur.

  Kabuk birden çok VSPackages barındırdığından, her VSPackage 'ı yoklamak için komut durumunu belirlemede gerekliyse, kabuğun performansı kaçınılmaz. Bunun yerine, değişiklik sırasında kullanıcı arabirimi değiştiğinde VSPackage, ortamı etkin bir şekilde bilgilendirmelidir. Güncelleştirme bildirimi hakkında daha fazla bilgi için bkz. [Kullanıcı arabirimini güncelleştirme](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Durum bildirim hatası
 Bir komut durum değişikliğinin ortamına bildirimde bulunan VSPackage hatası, Kullanıcı arabirimini tutarsız bir duruma getirebilir. Menü veya bağlam menüsü komutlarınızın Kullanıcı tarafından bir araç çubuğuna yerleştirilebileceğini unutmayın. Bu nedenle, Kullanıcı arabirimini yalnızca bir menü veya bağlam menüsü açıldığında güncelleştirmek yeterli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Uygulama](../../extensibility/internals/command-implementation.md)
