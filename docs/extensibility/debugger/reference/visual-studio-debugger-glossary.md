---
title: Visual Studio Hata ayıklayıcı sözlüğü | Microsoft Docs
description: bu makalede, Visual Studio hata ayıklama SDK 'sında, bağlama kesme noktası, kaussellik ve kod bağlamı gibi birçok terim açıklanmaktadır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bcbe68b0e8fd68d966bd1ed03d1b90aade9e579b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132333"
---
# <a name="visual-studio-debugger-glossary"></a>Visual Studio Hata Ayıklayıcısı Sözlüğü
Aşağıdakiler [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklama SDK 'sında kullanılan terimlerdir.

## <a name="terms"></a>Terimler
 bağlantılı kesme noktası, kodda ayarlanan kesme noktası için bir soyutlama. Bir ilişkili kesme noktası ve kod akışında bir kesme noktası yönergesi arasında bire bir ilişki vardır. Kod kaldırıldığında, bağlantılı kesme noktaları kesilebilir.

 causlık, birden çok fiziksel iş parçacığı, işlem ve makine arasında yürütülen bir mantıksal iş parçacığını izleme ve bu mantıksal iş parçacığının çağrı yığınını o iş parçacığı ömrü boyunca belirli bir noktada yeniden oluşturmak için olanak sağlar.

 kod bağlamı, hata ayıklama altyapısına bilinen kodda bir konumun soyutlamasını sağlar. Çoğu çalışma zamanı mimarilerinde, kod bağlamı bir programın yönerge akışındaki bir adrestir. Geleneksel olmayan dillerde, kodun yönergelerle temsil edilemeyebilir, bir kod bağlamı başka yollarla temsil edilebilir.

 kod yolu, bir dalın alındığı veya bir işlev çağrısının yapıldığı koddaki yürütme noktasını temsil eder. Yığın izlemesi aslında işlev çağrı kodu yollarının listesidir.

 çalışma zamanı mimarisinin hata ayıklamasına izin veren bir bileşen hata ayıklama altyapısı (DE). Bir hata ayıklama altyapısı, yorumlayıcı veya işletim sistemiyle birlikte çalışarak yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hata ayıklama hizmetleri sağlar.

 Belge bağlamı, hata ayıklama altyapısı tarafından bilinen kaynak dosya belgesinde bir konumun soyutlamasını sağlar. Çoğu dil için bir belge bağlamı, kaynak dosyadaki bir konumudur. Kaynak dosyanın metin olamayacağı geleneksel olmayan diller için bir belge bağlamı başka yollarla temsil edilebilir. Ayrıca bkz. *belge konumu*.

 belge konumu, IDE tarafından bilinen bir kaynak dosyasında konumun bir soyutlamasını sağlar. Çoğu dil için, bir belge konumu kaynak dosyadaki bir konum olur. Geleneksel olmayan diller için bir belge konumu başka yollarla gösterilebilir. Ayrıca bkz. *belge bağlamı*.

 hata kesme noktası bekleyen bir kesme noktasında hatayı açıklamak için bir soyutlama. Bir hata kesme noktası, bekleyen kesme noktasının konumundaki bir hatayı, bekleyen kesme noktasıyla ilişkili ifadeyi veya bekleyen kesme noktasının bir kod konumuna bağlamasını önleyen diğer bilgileri açıklayabilir.

 değerlendirme bağlamı, ifade değerlendirmesi için programlama bağlamının bir soyutlamasını sağlar. Genellikle, bir değerlendirme bağlamı bir kapsamdır. İfade bağlamında ifade değerlendirmesi yaparken ifade bağlamı, oluşturma noktasıyla eşleşen kapsam kuralları sağlar. Örneğin, yığın çerçevesinde oluşturulan bir ifade bağlamı yerel değişkenleri, yöntem parametrelerini, sınıf üyelerini (varsa) ve genel değişkenleri değerlendirmeye yönelik bağlamı sağlayacaktır.

 geçerli yığın çerçevesinde özel durum işleme mekanizması gerçekleşmese bile, bir hata ayıklama altyapısı tarafından kesilen özel durum ele alınmaz.

 Bu sistem kodu için kaynak kodu kullanılabilir olsa bile, yalnızca bir kullanıcıya ait kodu hata ayıklama ve sistem kodu gibi tüm ara kodları yok sayma kavramı.

 bekleyen kesme noktası, kod yüklenmeden önce, sırasında ve sonrasında kesme noktaları için bir soyutlama ve kesme noktalarını sanallaştırmaya yönelik bir yol sağlar. Bekleyen bir kesme noktası:

- Bir veya daha fazla programda koda bir kesme noktası bağlamak için gereken tüm bilgileri içerir.

- , Bir veya daha fazla programda birden çok kod konumuna bağlanamaz.

- Kendisini koda hiçbir şekilde bağlamamalıdır.

  Her kod yüklendiğinde, bir programdaki tüm bekleyen kesme noktaları bağlanıp bağlanamazlar. Bekleyen bir kesme noktası, bağlandığı tüm bağlı kesme noktalarını içeriyor olarak kabul edilir.

  fiziksel bir Win32 işlemini işleyin. Bir işlem birden çok program içerebilir. Ayrıca bkz. *Program*.

  belirli bir çalışma zamanı mimarisinin içinde çalışan tek bir ad alanı program. Ayrıca bkz. *işlem*.

  oturum hata ayıklama Yöneticisi (SDM), herhangi bir sayıdaki makinede birden çok işlemde bulunan sayıda programda hata ayıklamanın herhangi bir sayıda hata ayıklama altyapısını yönetir. Temel düzeyde, SDM hata ayıklama altyapılarının çoğullayıcısı olur. Ayrıca, SDM, IDE 'ye hata ayıklama oturumunun Birleşik bir görünümünü sağlar.

  yığın çerçevesi, belirli bir çerçevedeki hesaplamanın durumunu ve belirli bir iç içe işlev çağrılarının düzeyini temsil eder.

  en az bir programda çalışan yığın tabanlı yönerge yürütmesinin Genelleştirilmiş kavramına iş parçacığı.

  Uyarı kesme noktası bekleyen bir kesme noktasında uyarı tanımlamak için bir soyutlama. Uyarı kesme noktası, bekleyen kesme noktasının henüz bir kod konumuna bağlanmamasının nedenini açıklar. Bu, kodun, bekleyen kesme noktası tarafından tanımlanan konum veya başka bir nedenden dolayı henüz yüklenmemiş olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
