---
title: 'Nasıl yapılır: durum çubuğunu güncelleştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703141"
---
# <a name="how-to-update-the-status-bar"></a>Nasıl Yapılır: Durum Çubuğunu Güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Durum çubuğu** , bir veya daha fazla durum metin çizgisi veya göstergesi içeren birçok uygulama penceresinin alt kısmında bulunan bir denetim çubuğudur.  
  
### <a name="to-update-the-status-bar"></a>Durum çubuğunu güncelleştirmek için  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>Düzenleyicinin sağladığı form görünümü ve kod görünümü gibi her bir görünüm nesnesine (DocView) uygulayın.  
  
2. IDE çağırdığında <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> , yöntemlerini çağırarak **durum çubuğundaki** bilgileri güncelleştirin <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
    > [!NOTE]
    > IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> yalnızca belge pencereniz başlangıçta etkinleştirildiğinde çağrılır. Belge pencerenizin etkin olduğu sürenin geri kalanı için, düzenleyicinin durumu değiştikçe **durum çubuğu** bilgilerini güncelleştirmeniz gerekir.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bir **durum çubuğu** dört ayrı alan içerir:  
  
- Durum metni  
  
- İlerleme çubuğu  
  
- Animasyonlu simgesi  
  
- Düzenleyici bilgileri  
  
  Daha fazla bilgi için bkz. [durum çubukları](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>Belge pencereniz ETKINLEŞTIRILDIĞINDE IDE otomatik olarak uygulamanızın yöntemini çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
  VSPackage uygulayıcısı, durum çubuğundaki durum metnini güncelleştirmekten sorumludur. Durum metni alanı boş bir zaman ("") olarak ayarlandıysa, IDE bu dizeyi "READY" olarak sıfırlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Durum çubukları](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
