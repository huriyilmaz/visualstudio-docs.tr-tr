---
title: Türleri görsel tasarımcılara sunma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d6c0e163b751f1873fdb941e85c273dcc4fde5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691197"
---
# <a name="exposing-types-to-visual-designers"></a>Türleri Görsel Tasarımcıların Kullanımına Sunma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] görsel bir tasarımcıyı göstermek için tasarım zamanında sınıf ve tür tanımlarına erişimi olmalıdır. Sınıflar, geçerli projenin tüm bağımlılık kümesini (başvurular artı bunların bağımlılıkları) içeren önceden tanımlanmış bir derleme kümesinden yüklenir. Görsel tasarımcılarının özel araçlar tarafından oluşturulan dosyalarda tanımlanan sınıflara ve türlere erişmesi de gerekebilir.  
  
 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]Ve [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Proje sistemleri, geçici taşınabilir yürütülebilir dosyalar (geçici pes) aracılığıyla oluşturulan sınıflara ve türlere erişim desteği sağlar. Özel bir araç tarafından oluşturulan herhangi bir dosya, türlerin bu derlemelerden yüklenebilmesi ve tasarımcılara sunulanabilmesi için geçici bir derlemeye derlenebilir. Her bir özel aracın çıkışı ayrı bir geçici PE 'de derlenir ve bu geçici derlemenin başarısı veya başarısızlığı, yalnızca oluşturulan dosyanın derlenebilir olup olmamasına bağlıdır. Bir proje bir bütün olarak derlenmese de, tek tek geçici PEs tasarımcı tarafından kullanılabilir olmaya devam edebilir.  
  
 Proje sistemi, özel bir aracın çıkış dosyasında yapılan değişiklikleri izlemek için tam destek sağlar, bu değişiklikler özel aracı çalıştırmanın sonucudur. Özel araç her çalıştırıldığında, yeni bir geçici PE oluşturulur ve uygun bildirimler tasarımcılara gönderilir.  
  
> [!NOTE]
> Geçici program yürütülebilir oluşturma dosyası arka planda yapıldığından, derleme başarısız olursa kullanıcıya herhangi bir hata bildirilmemiştir.  
  
 Geçici PE desteğinden faydalanan özel araçlar aşağıdaki kurallara uymalıdır:  
  
- `GeneratesDesignTimeSource` kayıt defterinde 1 olarak ayarlanmalıdır.  
  
     Bu ayar olmadan hiçbir program yürütülebilir dosya derlemesi gerçekleşmez.  
  
- Oluşturulan kod, genel proje ayarıyla aynı dilde olmalıdır.  
  
     Geçici PE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> `GeneratesDesignTimeSource` kayıt defterinde 1 olarak ayarlanan istenen uzantı olarak özel araç raporlarından bağımsız olarak derlenir. Uzantının. vb,. cs veya. jsl; olması gerekmez. herhangi bir uzantı olabilir.  
  
- Özel araç tarafından oluşturulan kod geçerli olmalıdır ve yalnızca, yürütme tamamlandığında projede bulunan başvuruların kümesi kullanılarak derlenmelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> .  
  
     Geçici bir PE derlendiğinde, derleyiciye sunulan tek kaynak dosya özel araç çıktıdır. Bu nedenle, geçici bir PE kullanan özel bir araç, projedeki diğer dosyalardan bağımsız olarak derlenebilecek çıkış dosyaları üretmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [BuildManager nesnesine giriş](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Tek dosya oluşturucularını uygulama](../../extensibility/internals/implementing-single-file-generators.md)   
 [Projenin varsayılan ad alanını belirleme](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Tek Dosya Oluşturucuları Kaydetme](../../extensibility/internals/registering-single-file-generators.md)
