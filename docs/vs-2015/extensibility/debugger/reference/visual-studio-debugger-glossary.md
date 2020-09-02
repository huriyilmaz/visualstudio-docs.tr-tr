---
title: Visual Studio hata ayıklayıcısı sözlüğü | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 19d82f006bb1c37981f60e1a0b2710588eb0053c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204776"
---
# <a name="visual-studio-debugger-glossary"></a>Visual Studio Hata Ayıklayıcısı Sözlüğü
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Aşağıdakiler [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hata ayıklama SDK 'sında kullanılan terimlerdir.  
  
## <a name="terms"></a>Terimler  
 bağlantılı kesme noktası  
 Kodda ayarlanan kesme noktası için bir soyutlama. Bir ilişkili kesme noktası ve kod akışında bir kesme noktası yönergesi arasında bire bir ilişki vardır. Kod kaldırıldığında, bağlantılı kesme noktaları kesilebilir.  
  
 nedensellik  
 Birden çok fiziksel iş parçacığı, süreç ve makinede yürütülen bir mantıksal iş parçacığını izleme ve bu mantıksal iş parçacığının çağrı yığınını, o iş parçacığının yaşam süresinden belirli bir noktaya yeniden oluşturma yeteneği sağlar.  
  
 kod bağlamı  
 Hata ayıklama altyapısına bilinen kodda bir konumun soyutlamasını sağlar. Çoğu çalışma zamanı mimarilerinde, kod bağlamı bir programın yönerge akışındaki bir adrestir. Geleneksel olmayan dillerde, kodun yönergelerle temsil edilemeyebilir, bir kod bağlamı başka yollarla temsil edilebilir.  
  
 kod yolu  
 Bir dalın alındığı veya işlev çağrısının yapıldığı koddaki yürütme noktasını temsil eder. Yığın izlemesi aslında işlev çağrı kodu yollarının listesidir.  
  
 hata ayıklama altyapısı (DE)  
 Çalışma zamanı mimarisinin hata ayıklamasına izin veren bir bileşen. Bir hata ayıklama altyapısı, yorumlayıcı veya işletim sistemiyle birlikte çalışarak yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hata ayıklama hizmetleri sağlar.  
  
 Belge bağlamı  
 Hata ayıklama altyapısı tarafından bilinen kaynak dosya belgesinde bir konumun soyutlamasını sağlar. Çoğu dil için bir belge bağlamı, kaynak dosyadaki bir konumudur. Kaynak dosyanın metin olamayacağı geleneksel olmayan diller için bir belge bağlamı başka yollarla temsil edilebilir. Ayrıca bkz. *belge konumu*.  
  
 belge konumu  
 IDE tarafından bilinen kaynak dosyada bir konumun soyutlamasını sağlar. Çoğu dil için, bir belge konumu kaynak dosyadaki bir konum olur. Geleneksel olmayan diller için bir belge konumu başka yollarla gösterilebilir. Ayrıca bkz. *belge bağlamı*.  
  
 hata kesme noktası  
 Bekleyen bir kesme noktasında hatayı açıklamak için bir soyutlama. Bir hata kesme noktası, bekleyen kesme noktasının konumundaki bir hatayı, bekleyen kesme noktasıyla ilişkili ifadeyi veya bekleyen kesme noktasının bir kod konumuna bağlamasını önleyen diğer bilgileri açıklayabilir.  
  
 değerlendirme bağlamı  
 İfade değerlendirmesi için programlama bağlamının bir soyutlamasını sağlar. Genellikle, bir değerlendirme bağlamı bir kapsamdır. İfade bağlamında ifade değerlendirmesi yaparken ifade bağlamı, oluşturma noktasıyla eşleşen kapsam kuralları sağlar. Örneğin, yığın çerçevesinde oluşturulan bir ifade bağlamı yerel değişkenleri, yöntem parametrelerini, sınıf üyelerini (varsa) ve genel değişkenleri değerlendirmeye yönelik bağlamı sağlayacaktır.  
  
 yakalanamayan özel durum  
 Geçerli yığın çerçevesinde hiçbir özel durum işleme mekanizması gerçekleşmese bile, bir hata ayıklama altyapısı tarafından kesilen bir özel durum.  
  
 Adatmycode  
 Yalnızca bir kullanıcıya ait kodu hata ayıklama ve sistem kodu gibi tüm ara kodları yok sayma kavramı, kaynak kodu söz konusu sistem kodu için kullanılabilir olsa bile.  
  
 bekleyen kesme noktası  
 Kod yüklenmeden önce, sırasında ve sonrasında kesme noktaları için bir soyutlama ve kesme noktalarını sanallaştırmaya yönelik bir yol sağlar. Bekleyen bir kesme noktası:  
  
- Bir veya daha fazla programda koda bir kesme noktası bağlamak için gereken tüm bilgileri içerir.  
  
- , Bir veya daha fazla programda birden çok kod konumuna bağlanamaz.  
  
- Kendisini koda hiçbir şekilde bağlamamalıdır.  
  
  Her kod yüklendiğinde, bir programdaki tüm bekleyen kesme noktaları bağlanıp bağlanamazlar. Bekleyen bir kesme noktası, bağlandığı tüm bağlı kesme noktalarını içeriyor olarak kabul edilir.  
  
  process  
  Fiziksel bir Win32 işlemi. Bir işlem birden çok program içerebilir. Ayrıca bkz. *Program*.  
  
  program  
  Belirli bir çalışma zamanı mimarisinin içinde çalışan tek bir ad alanı. Ayrıca bkz. *işlem*.  
  
  oturum hata ayıklama Yöneticisi (SDM)  
  Herhangi bir sayıda makinede birden çok işlemde bulunan sayıda programda hata ayıklamanın herhangi bir sayıda hata ayıklama altyapısını yönetir. Temel düzeyde, SDM hata ayıklama altyapılarının çoğullayıcısı olur. Ayrıca, SDM, IDE 'ye hata ayıklama oturumunun Birleşik bir görünümünü sağlar.  
  
  yığın çerçevesi  
  Belirli bir çerçevedeki hesaplamanın durumunu ve belirli bir iç içe işlev çağrılarının düzeyini temsil eder.  
  
  thread  
  En az bir programda çalışan yığın tabanlı yönerge yürütmesinin Genelleştirilmiş kavramı.  
  
  Uyarı kesme noktası  
  Bekleyen bir kesme noktasında uyarı tanımlamak için bir soyutlama. Uyarı kesme noktası, bekleyen kesme noktasının henüz bir kod konumuna bağlanmamasının nedenini açıklar. Bu, kodun, bekleyen kesme noktası tarafından tanımlanan konum veya başka bir nedenden dolayı henüz yüklenmemiş olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
