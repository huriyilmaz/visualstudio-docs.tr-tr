---
title: Birlikte çalışma derlemelerini kullanarak komut durumunu belirleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc67123e082258932ab5df6613941f869d6049a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196782"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Birlikte Çalışma Bütünleştirilmiş Kodları Kullanarak Komut Durumunu Belirleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage, işleyebilmesi için komutların durumunu takip etmelidir. Ortam, VSPackage içinde işlenen bir komutun etkin veya devre dışı olacağını belirleyemiyor. Bu, ortama komut durumları hakkında bilgi vermek için VSPackage 'ın sorumluluğundadır. Örneğin, **Kes**, **Kopyala**ve **Yapıştır**gibi genel komutların durumu.  
  
## <a name="status-notification-sources"></a>Durum bildirim kaynakları  
 Ortam, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> arabirim uygulamanın VSPackage 'un bir parçası olan VSPackages ' yöntemi aracılığıyla komutlar hakkında bilgi alır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Ortam, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> iki koşulda VSPackage yöntemini çağırır:  
  
- Bir Kullanıcı ana menüyü veya bağlam menüsünü açtığında (sağ tıklanarak), ortam, durumlarını <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> belirlemede Bu menüdeki tüm komutlarda yöntemini yürütür.  
  
- VSPackage, ortamın geçerli kullanıcı arabirimini (UI) güncelleştirmesini istediğinde. Bu durum standart araç çubuğunda **kesme**, **kopyalama**ve **Yapıştırma** gruplandırması gibi, kullanıcıya şu anda görünür olan ve bağlam ve kullanıcı eylemlerine yanıt olarak etkin ve devre dışı bırakılmış olan komutlardır.  
  
  Kabuk birden çok VSPackages barındırdığından, her VSPackage 'ı yoklamak için komut durumunu belirlemede gerekliyse, kabuğun performansı kaçınılmaz. Bunun yerine, değişiklik sırasında kullanıcı arabirimi değiştiğinde VSPackage, ortamı etkin bir şekilde bilgilendirmelidir. Güncelleştirme bildirimi hakkında daha fazla bilgi için bkz. [Kullanıcı arabirimini güncelleştirme](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Durum bildirim hatası  
 Bir komut durum değişikliğinin ortamına bildirimde bulunan VSPackage hatası, Kullanıcı arabirimini tutarsız bir duruma getirebilir. Menü veya bağlam menüsü komutlarınızın Kullanıcı tarafından bir araç çubuğuna yerleştirilebileceğini unutmayın. Bu nedenle, Kullanıcı arabirimini yalnızca bir menü veya bağlam menüsü açıldığında güncelleştirmek yeterli değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Uygulama](../../extensibility/internals/command-implementation.md)
