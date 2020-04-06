---
title: Visual Studio Debugger Sözlük | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 954532311fe6b63fc288877a6d41722e6ea47581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713355"
---
# <a name="visual-studio-debugger-glossary"></a>Visual Studio Hata Ayıklayıcısı Sözlüğü
Hata [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Ayıklama SDK'da kullanılan terimler aşağıda verilmiştir.

## <a name="terms"></a>Koşullar
 bağlama kesme noktası Kodda ayarlanan bir kesme noktası için soyutlama. Bağlı kesme noktası ile kod akışında bir kesme noktası yönergesi arasında bire bir ilişki vardır. Kod boşaltıldığında, bağlı kesme noktaları çözülebilir.

 nedensellik Birden çok fiziksel iş parçacığı, işlem ve makine arasında yürütme mantıksal bir iş parçacığı izlemek ve bu iş parçacığının ömrü içinde herhangi bir noktada bu mantıksal iş parçacığı çağrı yığını nı yeniden oluşturma olanağı sağlar.

 kod bağlamı Hata ayıklama altyapısı tarafından bilinen koddaki bir konumun soyutlamasını sağlar. Çoğu çalışma zamanı mimarisi için kod bağlamı, programın yönerge akışındaki bir adrestir. Kodun yönergeler tarafından temsil edilemeyen geleneksel olmayan dilleriçin, kod bağlamı başka yollarla temsil edilebilir.

 kod yolu Bir dalı alınan veya işlev çağrısıyapılan koddaki bir yürütme noktasını temsil eder. Yığın izleme aslında işlev çağrı kodu yollarının bir listesidir.

 hata ayıklama motoru (DE) Çalışma zamanı mimarisinin hata ayıklanmasına izin veren bir bileşen. Hata ayıklama altyapısı, yorumlayıcı veya işletim sistemiyle birlikte çalışır ve yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hata ayıklama hizmetleri sağlar.

 belge bağlamı Hata Ayıklama altyapısı tarafından bilinen bir kaynak dosya belgesindeki bir pozisyonun soyutlamasını sağlar. Çoğu dil için belge bağlamı kaynak dosyasındaki bir konumdur. Kaynak dosyanın metin olmadığı geleneksel olmayan diller için, belge bağlamı başka yollarla temsil edilebilir. *Ayrıca*bkz.

 belge konumu IDE tarafından bilinen bir kaynak dosyadaki bir konumun soyutlamasını sağlar. Çoğu dil için belge konumu kaynak dosyasındaki bir konumdur. Geleneksel olmayan diller için belge konumu başka şekillerde temsil edilebilir. Ayrıca *bkz.*

 hata kesme noktası Bekleyen bir kesme noktasında bir hatayı açıklamak için soyutlama. Hata kesme noktası, bekleyen kesme noktasının konumundaki bir hatayı, bekleyen kesme noktasıyla ilişkili ifadeyi veya bekleyen kesme noktasının kod konumuna bağlanmasını engelleyen diğer bilgileri açıklayabilir.

 değerlendirme bağlamı Ifade değerlendirmesi için bir programlama bağlamının soyutlanması sağlar. Genellikle, bir değerlendirme bağlamı bir kapsamdır. İfade bağlamında ifade değerlendirmesi yaparken, ifade bağlamı oluşturma noktasıyla eşleşen kapsam kuralları sağlar. Örneğin, yığın çerçevesinde oluşturulan bir ifade bağlamı, yerel değişkenleri, yöntem parametrelerini, sınıf üyelerini (varsa) ve genel değişkenleri değerlendirmek için bağlamı sağlar.

 yakalanan özel durum Geçerli yığın çerçevesinde hiçbir özel durum işleme mekanizması yerinde olsa bile, hata ayıklama altyapısı tarafından yakalanan bir özel durum.

 JustMyCode Kaynak kodu bu sistem kodu için kullanılabilir olsa bile, yalnızca bir kullanıcıya ait kodu hata ayıklama ve sistem kodu gibi tüm ara kodları yok sayma kavramı.

 bekleyen kesme noktası Kod yüklenmeden önce, sırasında ve sonrasında kesme noktaları için bir soyutlama ve kesme noktalarını sanallaştırmanın bir yolunu sağlar. Bekleyen bir kesme noktası:

- Bir veya daha fazla programda bir kesme noktasını koda bağlamak için gereken tüm bilgileri içerir.

- Bir veya daha fazla programda birden çok kod konumuna bağlanabilir.

- Asla kendini koda bağlamaz.

  Kod yüklenir her zaman, bir programda bekleyen tüm kesme noktaları bağlanıp bağlanamayacaklarını görmek için denetlenir. Bekleyen bir kesme noktasının, bağladığının tüm bağlı kesme noktalarını içerdiği söylenir.

  fiziksel bir Win32 işlemi. Bir işlem birden çok program içerebilir. *Ayrıca*bkz.

  program Belirli bir çalışma zamanı mimarisi içinde çalışan tek bir ad alanı. *Ayrıca*bkz.

  oturum hata ayıklama yöneticisi (SDM) Herhangi bir sayıda makinede birden çok işlemdeki herhangi bir sayıda programda hata ayıklama hata ayıklama olan herhangi bir sayıda hata ayıklama motorunu yönetir. Temel düzeyde, SDM hata ayıklama motorlarının bir çoklayıcısidir. Ayrıca, SDM IDE'ye hata ayıklama oturumunun birleşik bir görünümünü sağlar.

  yığın çerçevesi Belirli bir çerçevedeki hesaplama durumunu ve iç içe geçirilmiş işlev çağrılarının belirli düzeyini temsil eder.

  thread En az bir programda çalışan yığın tabanlı yönerge yürütme genelleştirilmiş kavramı.

  uyarı kesme noktası Bekleyen bir kesme noktasında bir uyarıyı açıklamak için soyutlama. Uyarı kesme noktası, bekleyen kesme noktasının henüz bir kod konumuna bağlı olmamasının nedenini açıklar. Bu, kodun bekleyen kesme noktası tarafından açıklanan konum için henüz yüklenmemiş olması veya başka bir nedenle olması olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
