---
title: Nesnelerin stilini değiştirme
titleSuffix: Blend for Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f38bfc7a6899ff1d61b8103204bb58df5c5106a6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592954"
---
# <a name="modify-the-style-of-objects-in-blend-for-visual-studio"></a>Visual Studio için Blend içindeki nesnelerin stilini değiştirme

Bir nesneyi özelleştirmenin en kolay yolu **Özellikler** bölmesinde özellikleri ayarlamaya yönelik olur.

Ayarları veya ayar gruplarını yeniden kullanmak istiyorsanız, yeniden kullanılabilir bir kaynak oluşturun. Bu bir *Stil*, *şablon*veya özel renk gibi basit bir öğe olabilir. Ayrıca, bir denetimin durumuna göre farklı şekilde görünmesini sağlayabilirsiniz. Örneğin, Kullanıcı üzerini tıklattığında bir düğme yeşile dönüşür.

## <a name="brushes-modify-the-appearance-of-an-object"></a>Fırçalar: bir nesnenin görünümünü değiştirme

Görünümünü değiştirmek istiyorsanız nesneye bir fırça uygulayın.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Bir nesne üzerinde yinelenen bir görüntüyü veya kalıbı boyama

*Döşeme fırçası*kullanarak bir nesne üzerinde yinelenen bir görüntüyü veya kalıbı boyayın.

Bir kutucuk fırçası oluşturmak için, bir *görüntü fırçası*, *Çizim Fırçası*veya *görsel fırça* kaynağı oluşturarak başlarsınız.

Görüntü kullanarak bir görüntü fırçası oluşturun. Aşağıdaki çizimlerde, görüntü fırçası, görüntü fırçası döşeli ve görüntü fırçasının çevrilmiş olarak gösterildiği gösterilmektedir.

![Görüntü fırçası](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![mage fırçası döşeli](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![Görüntü fırçası çevrilmiş](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

Yol veya şekil gibi bir vektör çizimi kullanarak bir çizim Fırçası oluşturun. Aşağıdaki çizimler çizim Fırçası, çizim Fırçası döşeli ve çizim fırçasını çevrilmiş olarak gösterir.

![Çizim Fırçası](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![Çizim Fırçası döşeli](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![Çizim Fırçası çevrilmiş](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

Düğme gibi bir denetimden görsel fırça oluşturun. Aşağıdaki çizimlerde görsel fırça ve görsel fırça döşeli gösterilmektedir.

![Görsel fırça](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![Görsel fırça döşeli](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>Stiller ve şablonlar: denetimler arasında tutarlı bir görünüm oluşturma

Bir denetimin görünümünü ve davranışını bir kez tasarlayabilir ve bu tasarımı farklı denetimlere uygulayabilir, böylece bunları ayrı ayrı tutmak zorunda kalmazsınız.

**Bir stil kullanmanız gerekir mi?** : yalnızca varsayılan özellikleri (örneğin, bir düğmenin rengi) ayarlamak istiyorsanız, bir *Stil*kullanın. Bir stili uyguladıktan sonra bile bir denetimi değiştirebilirsiniz.

**Bir şablon kullanmanız gerekir mi?** : bir denetimin yapısını değiştirmek istiyorsanız, bir *şablon*kullanın. Bir grafiği veya logoyu bir düğmeye dönüştürmeyi düşünün. Bir şablonu ona uyguladıktan sonra bir denetimi değiştiremezsiniz.

### <a name="create-a-template-or-style"></a>Şablon veya stil oluşturma

Şablon oluşturmanın iki yolu vardır. Çalışma yüzeyinizdeki herhangi bir nesneyi bir denetime dönüştürebilir veya şablonunuzu varolan bir denetime dayandırdırabilirsiniz.

Herhangi bir nesneyi bir denetim şablonuna dönüştürmek için, nesneyi seçin ve ardından **Araçlar** menüsünde **Denetim yap**' ı seçin.

Şablonunuzu varolan bir denetime dayandırmak istiyorsanız çalışma yüzeyinde bir nesne seçin. Sonra, çalışma yüzeyinin üst kısmında, içerik haritası düğmesini seçin, **Şablonu Düzenle**' yi seçin ve ardından **bir kopyayı Düzenle** veya **boş oluştur**' u seçin.

![Şablon menüsünü Düzenle](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

Bir stil oluşturmak için, nesneyi seçin ve ardından **nesne** menüsünde **stili Düzenle**' yi seçin ve ardından **bir kopyayı Düzenle** veya **boş oluştur**' u seçin.

- Varsayılan stille veya denetimin şablonuyla başlamak için **bir kopyayı Düzenle** ' yi seçin.

- Sıfırdan başlamak için **boş oluştur** ' a tıklayın.

**Geçerli öğeyi Düzenle** seçeneği yalnızca önceden oluşturduğunuz bir stili veya şablonu düzenlediğinizde görüntülenir. Hala varsayılan bir sistem şablonu kullanan bir denetim için görüntülenmez.

**Stil kaynağı oluştur** iletişim kutusunda, daha sonra kullanabilmeniz için stili veya şablonu adlandırın ya da stili veya şablonu bu türün tüm denetimlerine uygulayabilirsiniz.

![Stil kaynağı oluştur iletişim kutusu](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> Her denetim türü için stil veya şablon oluşturamazsınız. Bir denetim bunları desteklemiyorsa, içerik haritası düğmesi çalışma yüzeyi üzerinde görünmez.
> Ana belgenizin düzenlenme kapsamına dönmek için, kapsamı **geri** Döndür ' e tıklayarak ![kapsamını simgeye](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png)döndürün.

### <a name="apply-a-style-or-template-to-a-control"></a>Denetime stil veya şablon uygulama

[Nesneler ve zaman çizelgesi](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) penceresinde bir nesneye sağ tıklayın, **Şablonu Düzenle**' yi ve ardından **kaynağı Uygula**' yı seçin.

![Kaynak menüsünü Uygula](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>Bir denetimin varsayılan stilini veya şablonunu geri yükleme

Denetimi seçin ve **Özellikler** **penceresinde **Stil** veya **şablon** özelliğini bulun. **Gelişmiş Seçenekler**' i seçin ve ardından kısayol menüsünde **Sıfırla** ' ya tıklayın.

## <a name="visual-states"></a>Görsel durumlar

Görsel durumlar, bir denetimin görünüşünü durumunu temel alarak değiştirmenize olanak sağlar. Denetimlerin kullanıcı etkileşimlerine göre farklı görsel görünümleri olabilir. Örneğin, bir Kullanıcı üzerini tıklattığında bir düğmeyi yeşil hale getirebilirsiniz veya bir animasyon çalıştırabilirsiniz. Geçişleri kullanarak görsel durumlar arasındaki süreyi kısaltın veya uzatın.

![Fare durumuna göre](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

[WPF denetimlerinizin durumunu yönetmek](https://www.youtube.com/watch?v=m0PlkF5i6uw)](../designers/media/bldadminconsoleinitialconfigicon.PNG) **kısa bir video Izleyin:** ![Oynat düğmesi.

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>Kaynaklar: renkler, stiller ve şablonlar oluşturun ve daha sonra yeniden kullanın

Yalnızca projenizde bir şeyi bir kaynağa dönüştürebilirsiniz. Bir kaynak, yalnızca uygulamanızdaki farklı yerlerde yeniden kullanabileceğiniz bir nesnedir. Örneğin, bir kez renk oluşturabilir, bunu kaynak yapabilir ve daha sonra bu rengi çeşitli nesnelerde kullanabilirsiniz. Bu nesnelerin tümünün rengini değiştirmek için, yalnızca renk kaynağını değiştirmeniz yeterlidir.

![Rengi kaynağa dönüştür düğmesi](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![Renk kaynağı oluştur iletişim kutusu](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
