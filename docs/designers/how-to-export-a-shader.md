---
title: 'Nasıl Yapılır: Gölgelendiriciyi Dışarı Aktarma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c05e40b76d60a5602cee1cb67b5c3094fb94d249
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635544"
---
# <a name="how-to-export-a-shader"></a>Nasıl yapılır: gölgelendiriciyi dışarı aktarma

Bu makalede, uygulamanızda kullanabilmeniz için bir yönlendirilmiş grafik gölgelendirici dili (DGSL) gölgelendiriciyi dışarı aktarmak üzere **Gölgelendirici Tasarımcısının** nasıl kullanılacağı gösterilmektedir.

## <a name="export-a-shader"></a>Gölgelendiriciyi dışarı aktarma

Gölgelendirici tasarımcısını kullanarak bir gölgelendirici oluşturduktan ve uygulamanızda kullanabilmeniz için, bunu grafik API 'nizin anlayacağı bir biçimde dışarı aktarmanız gerekir. Farklı ihtiyaçları karşılamak için bir gölgelendiriciyi farklı yollarla dışarı aktarabilirsiniz.

1. Visual Studio 'da bir **Görsel Gölgelendirici Grafiği (. dgsl)** dosyası açın.

     Açmak için bir **Görsel Gölgelendirici Grafiği (. dgsl)** dosyanız yoksa, [nasıl yapılır: temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md)bölümünde açıklandığı gibi bir tane oluşturun.

2. **Gölgelendirici Tasarımcısı** araç çubuğunda **Gelişmiş**  > **dışarı** **Aktar  >  dışarı aktar '** ı seçin. **Gölgelendiriciyi dışarı aktar** iletişim kutusu görünür.

3. **Farklı kaydet türü** aşağı açılan listesinde, dışarı aktarmak istediğiniz biçimi seçin.

     Seçebileceğiniz biçimler şunlardır:

     **HLSL piksel gölgelendiricisi (\*. hlsl)** Gölgelendiriciyi üst düzey gölgelendirici dili (HLSL) kaynak kodu olarak dışa aktarır. Bu seçenek, bir uygulamaya dağıtıldıktan sonra bile gölgelendiriciyi daha sonra değiştirmeyi mümkün kılar. Bu, son kullanıcı sorunlarına göre kodun hata ayıklamasının ve düzeltme ekinin değiştirilmesini kolaylaştırır, ancak bir kullanıcının bir rekabet oyunundaki bir avantaj elde etmek gibi, gölgelendiriciyi istenmeyen yollarla değiştirmesini da kolaylaştırır. Ayrıca, gölgelendirici yükleme süresini de artırabilir.

     **Derlenmiş piksel gölgelendiricisi (\*. CSO)** Gölgelendiriciyi HLSL bayt olarak dışa aktarır. Bu seçenek, bir uygulamaya dağıtıldıktan sonra bile gölgelendiriciyi daha sonra değiştirmeyi mümkün kılar. Bu, son kullanıcı sorunlarına göre kodun hata ayıklamasını ve düzeltme ekini daha kolay hale getirir, ancak gölgelendirici önceden derlendiğinden, gölgelendirici uygulama tarafından yüklendiğinde ek çalışma zamanı ek yüküne neden olmaz. Yeterli nitelikli kullanıcılar gölgelendiriciyi istenmeyen yollarla değiştirebilir, ancak gölgelendirici derlenerek bunu önemli ölçüde daha zor hale getirebilirsiniz.

     **Üst bilgi (\*. h) C++**  Gölgelendiriciyi, HLSL bytecode içeren bir bayt dizisini tanımlayan C stili bir üstbilgi olarak dışa aktarır. Bu seçenek, düzeltmenin test etmek için uygulamanın yeniden derlenmesi gerektiğinden, son kullanıcı sorunlarına göre kodun hata ayıklamasını ve düzeltme ekini oluşturmak için daha fazla zaman alabilir. Ancak, bu seçenek mümkün olmasa da, bir uygulamada dağıtıldıktan sonra gölgelendiriciyi değiştirmek zor olsa da, gölgelendiriciyi istenmeyen yollarla değiştirmek isteyen bir kullanıcıya çok fazla zorluk gösterir.

4. **Dosya adı** Birleşik giriş kutusunda, dışarıya aktarılmış gölgelendirici için bir ad belirtin ve ardından **Kaydet** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)