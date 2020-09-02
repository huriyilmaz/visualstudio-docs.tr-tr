---
title: 'Nasıl yapılır: gölgelendiriciyi dışarı aktarma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2225ce416fed4e97e998a50f70a0dc4c25908476
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664468"
---
# <a name="how-to-export-a-shader"></a>Nasıl Yapılır: Gölgelendiriciyi Dışarı Aktarma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, uygulamanızda kullanabilmeniz için bir yönlendirilmiş grafik gölgelendirici dili (DGSL) gölgelendiriciyi dışarı aktarmak üzere Gölgelendirici Tasarımcısının nasıl kullanılacağını gösterir.

 Bu belgede bu etkinlik gösterilmektedir:

- Gölgelendiriciyi dışarı aktarma

## <a name="exporting-a-shader"></a>Gölgelendiriciyi dışarı aktarma
 Gölgelendirici tasarımcısını kullanarak bir gölgelendirici oluşturduktan ve uygulamanızda kullanabilmeniz için, bunu grafik API 'nizin anlayacağı bir biçimde dışarı aktarmanız gerekir. Farklı ihtiyaçları karşılamak için bir gölgelendiriciyi farklı yollarla dışarı aktarabilirsiniz.

#### <a name="to-export-a-shader"></a>Gölgelendiriciyi dışarı aktarmak için

1. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bir **Görsel Gölgelendirici Grafiği (. dgsl)** dosyası açın.

     Açmak için bir **Görsel Gölgelendirici Grafiği (. dgsl)** dosyanız yoksa, [nasıl yapılır: temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md)bölümünde açıklandığı gibi bir tane oluşturun.

2. **Gölgelendirici Tasarımcısı** araç çubuğunda **Gelişmiş**, **dışarı**aktar, **farklı ver**' i seçin. **Gölgelendiriciyi dışarı aktar** iletişim kutusu görüntülenir.

3. **Farklı kaydet türü** aşağı açılan listesinde, dışarı aktarmak istediğiniz biçimi seçin.

     Seçebileceğiniz biçimler şunlardır:

     **HLSL piksel gölgelendiricisi ( \* . hlsl)** , gölgelendiriciyi üst düzey gölgelendirici dili (HLSL) kaynak kodu olarak dışa aktarır. Bu seçenek, bir uygulamaya dağıtıldıktan sonra bile gölgelendiriciyi daha sonra değiştirmeyi mümkün kılar. Bu, son kullanıcı sorunlarına göre kodun hata ayıklamasının ve düzeltme ekinin değiştirilmesini kolaylaştırır, ancak bir kullanıcının bir rekabet oyunundaki bir avantaj elde etmek gibi, gölgelendiriciyi istenmeyen yollarla değiştirmesini da kolaylaştırır. Ayrıca, gölgelendirici yükleme süresini de artırabilir.

     **Derlenmiş piksel gölgelendiricisi ( \* . CSO)** , gölgelendiriciyi hlsl bytecode olarak dışa aktarır. Bu seçenek, bir uygulamada dağıtıldıktan sonra bile gölgelendiriciyi daha sonra değiştirmek mümkün olur. Bu, son kullanıcı sorunlarına göre kodun hata ayıklamasını ve düzeltme ekini daha kolay hale getirir, ancak gölgelendirici önceden derlendiğinden, gölgelendirici uygulama tarafından yüklendiğinde ek çalışma zamanı ek yüküne neden olmaz. Yeterli nitelikli kullanıcılar gölgelendiriciyi istenmeyen yollarla değiştirebilir, ancak gölgelendirici derlenerek bunu önemli ölçüde daha zor hale getirebilirsiniz.

     **C++ üstbilgisi ( \* . h)** , gölgelendiriciyi hlsl bytecode içeren bir bayt dizisini tanımlayan C stili bir üstbilgi olarak dışa aktarır. Bu seçenek, düzeltmenin test etmek için uygulamanın yeniden derlenmesi gerektiğinden, son kullanıcı sorunlarına göre kodun hata ayıklamasını ve düzeltme ekini oluşturmak için daha fazla zaman alabilir. Ancak, bu seçenek mümkün olmasa da, bir uygulamada dağıtıldıktan sonra gölgelendiriciyi değiştirmek zor olsa da, gölgelendiriciyi istenmeyen yollarla değiştirmek isteyen bir kullanıcıya çok fazla zorluk gösterir.

4. **Dosya adı** Birleşik giriş kutusunda, dışarıya aktarılmış gölgelendirici için bir ad belirtin ve ardından **Kaydet** düğmesini seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: temel renk gölgelendirici](../designers/how-to-create-a-basic-color-shader.md) [Gölgelendirici Tasarımcısı](../designers/shader-designer.md) oluşturma
