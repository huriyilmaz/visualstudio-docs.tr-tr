---
title: 'Nasıl Yapılır: Gölgelendiriciyi Dışarı Aktarma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4a3aec047238786a60b1261415acccfed521695
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589441"
---
# <a name="how-to-export-a-shader"></a>Nasıl yapılır: Gölgeli dışa aktarma

Bu makalede, uygulamanızda kullanabilmeniz için Yönlendirilmiş Grafik Shader Dili (DGSL) shader'ı dışa aktarmak için **Shader Designer'ın** nasıl kullanılacağı gösterilmektedir.

## <a name="export-a-shader"></a>Gölgelendiriciyi dışarı aktarma

Shader Designer'ı kullanarak bir gölgelendirme oluşturduktan ve uygulamanızda kullanmadan önce, grafik API'nizin anladığı bir biçimde dışa aktarmanız gerekir. Farklı gereksinimleri karşılamak için farklı şekillerde bir gölgeli dışa aktarabilirsiniz.

1. Visual Studio'da **Visual Shader Graph (.dgsl)** dosyalarını açın.

     Açmak için **Görsel Shader Graph (.dgsl)** dosyanız yoksa, nasıl açıklanırsa bir dosya [oluşturun: Temel bir renk shader oluşturun.](../designers/how-to-create-a-basic-color-shader.md)

2. **Shader Designer** araç çubuğunda **Gelişmiş** > **Dışa Aktarma** > **Olarak'ı**seçin. Dışa Aktarma **Shader** iletişim kutusu görüntülenir.

3. Açılan yazı **listesinde Kaydet'te,** dışa aktarmak istediğiniz biçimi seçin.

     Seçebileceğiniz biçimler şunlardır:

     **HLSL Piksel Shader (\*.hlsl)** Shader'ı Yüksek Düzeyli Shader Dili (HLSL) kaynak kodu olarak dışa aktarım. Bu seçenek, bir uygulamada dağıtıldıktan sonra bile gölgeyi daha sonra değiştirmeyi mümkün kılar. Bu, kodu son kullanıcı sorunlarına göre hata ayıklamayı ve düzeltmeyi kolaylaştırabilir, ancak kullanıcının gölgeparçanızı istenmeyen şekillerde değiştirmesini de kolaylaştırır(örneğin, rekabetçi bir oyunda haksız bir avantaj elde etmek). Ayrıca gölgeleyicinin yükleme süresini de artırabilir.

     **Derlenmiş Piksel\*Shader ( .cso)** Shader'i HLSL bytecode olarak dışa aktarım. Bu seçenek, bir uygulamada dağıtıldıktan sonra bile gölgeyi daha sonra değiştirmeyi mümkün kılar. Bu, kodu son kullanıcı sorunlarına göre hata ayıklamayı ve düzeltmeyi kolaylaştırabilir, ancak gölgeli önceden derlendiğinden, gölgeleyici uygulama tarafından yüklendiğinde fazladan çalışma süresi ek yüküne neden olmaz. Yeterince yetenekli kullanıcılar hala istenmeyen şekillerde shader değiştirebilirsiniz, ancak shader derleme bu önemli ölçüde daha zor hale getirir.

     **C++ Üstbilgi\*( .h)** Shader'ı HLSL bayt kodu içeren bir bayt dizisini tanımlayan C stili üstbilgi olarak dışa aktarım. Bu seçenek, düzeltmeyi test etmek için uygulamanın yeniden derlemesi gerektiğinden, kodu hata ayıklama ve son kullanıcı sorunlarına göre düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi düzeltmeyi daha fazla zaman alabilir. Ancak, bu seçenek, bir uygulamada dağıtıldıktan sonra gölgeleyiciyi değiştirmeyi zorlaştırdığından, gölgeyi istenmeyen şekillerde değiştirmek isteyen bir kullanıcıya en büyük zorluk getirir.

4. Dosya **adı** açılan kutusunda, dışa aktarılan gölgeleyici için bir ad belirtin ve sonra **Kaydet** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel renk shader oluşturma](../designers/how-to-create-a-basic-color-shader.md)
- [Shader Tasarımcısı](../designers/shader-designer.md)
