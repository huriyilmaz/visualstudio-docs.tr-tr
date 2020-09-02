---
title: "PTV 'leri kullanmaya başlama: kodlamaya başlama (projeler) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 7
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 28622f290d82f86bf3d18cc4f40cfcfc8e953dad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537159"
---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>PTVS Kullanmaya Başlarken: Kod Yazmaya Başlama (Projeler)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio için Python Araçları (PTV) kodunuzu yönetmenize yardımcı olur. 
 
 Bu yönergeleri, çok kısa bir [youtube videosunda](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2)izleyebilirsiniz. 
 
 Daha önce Python kullandıysanız, projenizin dosyaları diske nasıl yerleşeceğine göre tanımlandığını bilirsiniz. Bu, düz Python projeleri için harika çalışmaktadır, ancak daha fazla dosyaya (JavaScript, birim testleri ve derleme betikleri içeren Web sayfaları) sahip olduğunuzda, dosya sistemleri bir bit sınırlandırmaya başlayabilir. Visual Studio, projeleri kullanarak üç şey elde etmenizi sağlar. 
 
- Kritik dosyaları belirler. Önemli dosyalar bir sürüm denetim sistemine (kaynak dosyaları, kaynaklar, vb.) iade edersiniz, ancak derleme çıkışı olarak oluşturulan dosyalar değildir. Önemli dosyalar aynı zamanda başka bir bilgisayara kopyalayacaklarınız olduğundan, başka birinin uygulamanızda çalışmasını sağlayabilirsiniz. 
 
- Dosyaların nasıl kullanılacağını belirtin. Dosyalar her değiştiğinde bir aracın işlemesi gereken dosyalara sahip olabilirsiniz. Visual Studio projeleri, bu bilgileri yakalayabilir 
 
- Bileşenlerinizin sınırlarını tanımlayın. Uygulamanızda birden çok bileşen varsa, her birini ayrı bir projeye yerleştirebilirsiniz. Bunlar sonunda, farklı derleme veya hata ayıklama ayarları kullanılarak oluşturulmuş farklı sunuculara dağıtılabilir ya da C++ veya Node.js gibi Visual Studio tarafından desteklenen başka bir dil kullanılarak yazılabilir. 
 
  Başlamanıza yardımcı olacak birkaç proje şablonu vardır. Üzerinde çalışmak istediğiniz Python kodunuz zaten varsa, mevcut kod Sihirbazı, tüm dosyalarınızı içeren bir proje oluşturmanıza yardımcı olur. Bazı popüler çerçeveler için birden çok Web projesi mevcuttur. PTV örnekleri paketinde daha fazla şablon bulunabilir. Belirtilen Web şablonlarının diğer çerçeveler ile çalışmasını sağlamak için seçenekler vardır. Python uygulama şablonu temiz, boş bir projem. Başlamanızı sağlamak için bir modül vardır. 
 
  Visual Studio, tüm dosyalar, arama yolları ve Python ortamları dahil olmak üzere Çözüm Gezgini penceresinde açık projelerinizi gösterir. Yeni öğeler eklemek için, proje klasörünüzü ve bağlam menüsünden (sağ işaretçi düğmesine basın), Ekle ' yi ve ardından yeni öğe ' yi seçin. İletişim kutusunda herhangi bir öğeyi seçebilir, öğenin adını özelleştirebilir ve öğeyi projeye ekleyebilirsiniz. 
 
  Çözüm Gezgini sürükleyip bırakabilirsiniz. Zaten proje dizin yapınıza dosya kopyaladıysanız, Çözüm Gezgini en üstünde tüm dosyaları göster seçeneğini belirleyebilirsiniz. Ardından, eklemek istediğiniz öğeleri seçebilir ve bağlam menüsünden projeye dahil et ' i seçin. 
 
  Bu yönergeleri, çok kısa bir [youtube videosunda](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2)izleyebilirsiniz. 
 
## <a name="see-also"></a>Ayrıca Bkz. 
 [Wiki belgeleri](https://github.com/Microsoft/PTVS/wiki/Projects) [PTV 'leri kullanmaya başlama ve derin video](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
