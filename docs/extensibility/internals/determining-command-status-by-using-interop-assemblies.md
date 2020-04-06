---
title: Interop Montajları Kullanarak Komut Durumunu Belirleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708708"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Interop derlemelerini kullanarak komut durumunu belirleme
BIR VSPackage işleyebilir komutların durumunu izlemek gerekir. Ortam, VSPackage'ınıziçinde işlenen bir komutun ne zaman etkinleştirilen veya devre dışı bırakıldığını belirleyemez. Örneğin, **Kesme,** **Kopyala**ve **Yapıştır**gibi genel komutların durumu gibi komut durumları hakkında ortamı bilgilendirmek VSPackage'ınızın sorumluluğundadır.

## <a name="status-notification-sources"></a>Durum bildirim kaynakları
 Ortam, VSPackage'ın <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabiriminin uygulanmasının bir parçası olan VSPackage yöntemi aracılığıyla komutlar hakkında bilgi alır. Ortam, VSPackage yöntemini <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> iki koşulaltında çağırır:

- Bir kullanıcı bir ana menü veya bağlam menüsü (sağ tıklatarak) <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> açtığında, ortam durumlarını belirlemek için bu menüdeki tüm komutlarda yöntemi yürütür.

- VSPackage ortam geçerli kullanıcı arabirimini (UI) güncelleştirmesini istediğinde. Bu güncelleştirme, standart araç çubuğunda **Kesme,** **Kopyalama**ve **Yapıştır** gruplandırma gibi kullanıcı tarafından şu anda görülebilen komutların bağlam ve kullanıcı eylemlerine yanıt olarak etkinleştirilip devre dışı bırakıldığı şeklinde gerçekleşir.

  Kabuk birden çok VSPackages barındırdığından, komut durumunu belirlemek için her VSPackage'ı yoklaması gerekirse kabuğun performansı kabul edilemez şekilde düşer. Bunun yerine, VSPackage'ınız değişiklik sırasında UI değiştiğinde ortamı etkin bir şekilde bildirmelidir. Güncelleştirme bildirimi hakkında daha fazla bilgi için [bkz.](../../extensibility/updating-the-user-interface.md)

## <a name="status-notification-failure"></a>Durum bildirimi hatası
 VSPackage'ınızın bir komut durumu değişikliğinin ortamını bildirmemesi UI'yi tutarsız bir duruma yerleyebilir. Menü veya bağlam menüsü komutları herhangi kullanıcı tarafından bir araç çubuğuna yerleştirilebilir unutmayın. Bu nedenle, ui'yi yalnızca bir menü veya bağlam menüsü açıldığında güncelleştirmek yeterli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Uygulama](../../extensibility/internals/command-implementation.md)
