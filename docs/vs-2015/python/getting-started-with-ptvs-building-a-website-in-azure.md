---
title: "PTV 'leri kullanmaya başlama: Azure 'da Web sitesi oluşturma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 288fb24c9c1c4ddee1cb59a968e717531e274af1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300590"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>PTVS Kullanmaya Başlarken: Azure’da Web Sitesi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Azure 'da bir Python web sitesi oluşturmaya hemen başlayın.  
  
 Bu yönergeleri, çok kısa bir [youtube videosunda](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6)izleyebilirsiniz.  
  
 Yeni proje ile Başlat... iletişim kutusu ve Python projeleri altında şişe Web projesi ' ni seçin.  Bu [şişe](http://bottlepy.org/docs/dev/index.html) şablonu, [önyükleme çerçevesini](https://getbootstrap.com/)temel alan bir başlatıcı sitedir.  Projeyi oluştururken, Visual Studio bir sanal ortama bağımlılıklar (Bu durumda şişe) yüklemenizi ister.  Bir Azure Web sitesine dağıtmakta olduğunuzdan, sitenizin işlemi için gerekli bitleri dağıtmak üzere bir sanal ortama bağımlılıkları eklemeniz gerekir.  Ayrıca, ortamınızı Python 2,7 veya 3,4 32 bit temelinde temel almanız gerekir.  Projeyi oluşturduktan sonra, sitenizi yerel olarak çalıştırmaya başlamak için F5 ' e basın.  
  
 Siteyi Azure 'da denemek kolaydır.  Azure aboneliğiniz yoksa, [TRY.azurewebsites.net](https://trywebsites.azurewebsites.net/)kullanabilirsiniz.  Bu site, Azure Web sitelerini yalnızca sosyal oturum açma bilgileriyle bir saat boyunca denemek için basit bir yol sunar.  Kredi kartına ihtiyacınız yoktur.  Dili değiştir açılan menüsünde boş site şablonunu seçin ve Oluştur ' a tıklayın.  "Web uygulamanızla çalışma" altında yayımlama profilini Indir ' i seçin ve dosyayı Visual Studio ile kullanmak üzere kaydedin.  Ayrıca herhangi bir işletim sisteminden git kullanarak dağıtım yapabilirsiniz.  
  
 Visual Studio 'ya ve oluşturduğunuz projeye geri dönün.  Çözüm Gezgini proje düğümünü seçin, sağ işaretçi düğmesini seçin ve Yayımla ' yı seçin.  Azure aboneliğiniz varsa, sitelerinizi buradan yönetmek için iletişim kutusunda Microsoft Azure Web siteleri ' ne tıklayabilirsiniz.  Bu kılavuzda, az önce indirdiğiniz yayımlama profilini içeri aktarmak için Içeri Aktar ' ı seçin.  Yayımlama profilinde gerekli tüm bilgiler bulunduğundan, Yayımla ' yı seçebilirsiniz.  Birkaç saniye içinde yeni bir tarayıcı penceresi açılır ve siteniz Azure bulutu 'nda canlı olarak barındırılır.  
  
 Basit Web siteleri kolaydır, ancak Azure 'daki daha önemli Web uygulamaları hakkında daha fazla bilgi için, bu kanaldaki diğer kişilere (Başlarken veya derinlemesine bakış videonun sağ üst köşesinde bulunan bağlantı) ve aşağıdaki [gibi ayrıntılı bilgiler](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10) için bkz..  
  
 Bu yönergeleri, çok kısa bir [youtube videosunda](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6)izleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Wiki belgeleri](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [PTV 'Leri kullanmaya başlama ve derinlemesine bakış videoları](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
