---
title: Visual Studio Hata Ayıklayıcı Sözlüğü | Microsoft Docs
description: Bu makalede, hata ayıklama SDK'sında Visual Studio kesme noktası, nedensellik ve kod bağlamı gibi çeşitli terimler açıklanmıştır.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634697"
---
# <a name="visual-studio-debugger-glossary"></a>Visual Studio Hata Ayıklayıcısı Sözlüğü
Hata Ayıklama SDK'sı içinde [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] kullanılan terimler aşağıda velanmıştır.

## <a name="terms"></a>Terimler
 bağlı kesme noktası Kodda ayarlanmış bir kesme noktası için özet. Kod akışındaki bir bağlı kesme noktası ile kesme noktası yönergesi arasında bire bir ilişki vardır. Kod kaldırılan zaman, bağlı kesme noktaları bire bir kaldırılmış olabilir.

 nedensellik Birden çok fiziksel iş parçacığı, işlem ve makine arasında mantıksal bir yürütme iş parçacığını izleme ve bu mantıksal iş parçacığının çağrı yığınını o iş parçacığının yaşam süresinde herhangi bir noktada yeniden oluşturabilme olanağı sağlar.

 kod bağlamı Hata ayıklama altyapısı tarafından bilinen kodda bir konumun özetlerini sağlar. Çoğu çalışma zamanı mimarisi için kod bağlamı, bir programın yönerge akışındaki adrestir. Kodun yönergelerle temsili olmayan, koşulsuz diller için, bir kod bağlamı başka bir şekilde temsil olabilir.

 kod yolu Kodda bir dal alınarak veya işlev çağrısı yapılan yürütme noktasını temsil eder. Yığın izlemesi temelde işlev çağrısı kod yollarının listesidir.

 hata ayıklama altyapısı (DE) Çalışma zamanı mimarisinde hata ayıklamaya olanak sağlayan bir bileşen. Hata ayıklama altyapısı yorumlayıcı veya işletim sistemiyle birlikte çalışır ve yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hata ayıklama hizmetleri sağlar.

 belge bağlamı Hata ayıklama altyapısı tarafından bilinen bir kaynak dosya belgesinde bir konumun soyutlama sağlar. Çoğu dil için belge bağlamı, kaynak dosyada bir konum olur. Kaynak dosyanın metin olabileceği, koşulsuz diller için belge bağlamı başka bir şekilde temsil olabilir. Ayrıca *bkz. belge konumu.*

 belge konumu IDE tarafından bilinen bir kaynak dosyada yer alan konumun soyutlamalarını sağlar. Çoğu dil için belge konumu, kaynak dosyanın konumu olur. Koşulsuz diller için belge konumu başka yollarla temsil olabilir. Ayrıca *bkz. belge bağlamı.*

 hata kesme noktası Bekleyen kesme noktası hatasını açıklamaya bir özet. Hata kesme noktası, bekleyen kesme noktası konumu, bekleyen kesme noktasıyla ilişkili ifade veya bekleyen kesme noktası ile kod konumu bağlamasını engelleyen diğer bilgilerdeki bir hatayı açıklar.

 değerlendirme bağlamı İfade değerlendirmesi için bir programlama bağlamının soyutlama sağlar. Genellikle değerlendirme bağlamı bir kapsamdır. İfade bağlamında ifade değerlendirmesi yaparken ifade bağlamı, oluşturma noktasına uygun kapsam kuralları sağlar. Örneğin, bir yığın çerçevesinde oluşturulan ifade bağlamı yerel değişkenlerin, yöntem parametrelerinin, sınıf üyelerinin (varsa) ve genel değişkenlerin değerlendirilmesi için bağlam sağlar.

 kesme özel durumu Geçerli yığın çerçevesinde bir özel durum işleme mekanizması mevcut olsa bile bir hata ayıklama altyapısı tarafından kesme yapılan özel durum.

 JustMyCode Yalnızca bir kullanıcıya ait olan kodda hata ayıklama ve sistem kodu gibi tüm ara kodları yoksayma kavramı(bu sistem kodu için kaynak kod kullanılabilir olsa bile).

 bekleyen kesme noktası Kod yüklenmeden önce, sırasında ve sonrasında kesme noktaları için bir soyutlama sağlar ve kesme noktaları sanallaştırmanın bir yolunu sağlar. Bekleyen bir kesme noktası:

- Bir veya daha fazla programda koda kesme noktası bağlamak için gereken tüm bilgileri içerir.

- Bir veya daha fazla programda birden çok kod konumu bağlanabilir.

- Kendisini hiçbir zaman koda bağlamaz.

  Kod her yüklendiğinde, bir programda bekleyen tüm kesme noktaları bağlanıp bağlanamay olduklarını görmek için denetlenir. Bekleyen bir kesme noktası, bağ yaptığı tüm bağlı kesme noktaları içerdiği kabul edildi.

  işlem Fiziksel win32 işlemi. Bir işlem birden çok program içerebilir. Ayrıca bkz. *program.*

  program Belirli bir çalışma zamanı mimarisi içinde çalışan tek bir ad alanı. Ayrıca bkz. *işlemi.*

  oturum hata ayıklama yöneticisi (SDM) Herhangi bir sayıda makinede birden çok işlemde herhangi bir sayıda programda hata ayıklarken herhangi bir sayıda hata ayıklama altyapısını yönetir. Temel düzeyde SDM, hata ayıklama altyapılarının bir çok katsıcısıdır. Ayrıca, SDM IDE'de hata ayıklama oturumunun birleşik bir görünümünü sağlar.

  yığın çerçevesi Belirli bir çerçevede ve iç içe geçmiş işlev çağrılarının belirli bir düzeyindeki hesaplama durumunu temsil eder.

  iş parçacığı En az bir programda çalışan yığın tabanlı yönerge yürütme genelleştirilmişliği.

  uyarı kesme noktası Bekleyen bir kesme noktası içinde bir uyarıyı açıklamaya göre özet. Uyarı kesme noktası, bekleyen kesme noktası henüz bir kod konumuyla sınırlanmama nedenini açıklar. Bu, kodun beklemedeki kesme noktası tarafından açıklanan konum için veya başka bir nedenle henüz yüklenmemiş olması olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
