---
title: Blend 'de nesnelerin stilini değiştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0335efcb0c42c6fce06df448a0503457e79ec345
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664231"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Blend'de nesnlerin stilini değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir nesneyi özelleştirmenin en kolay yolu **Özellikler** bölmesinde özellikleri ayarlamaya yönelik olur.

 Ayarları veya ayar gruplarını yeniden kullanmak istiyorsanız, yeniden kullanılabilir bir kaynak oluşturun. Bu bir *Stil*, *şablon*veya özel renk gibi basit bir öğe olabilir. Ayrıca, bir denetimin durumuna göre farklı şekilde görünmesini sağlayabilirsiniz. Örneğin, Kullanıcı üzerini tıklattığında bir düğme yeşile dönüşür.

 **Bu konuda**:

- [Fırçalar: bir nesnenin görünümünü değiştirme](#Brushes)

- [Stiller ve şablonlar: denetimler arasında tutarlı bir görünüm oluşturma](#Styles)

- [Görsel durumlar: bir denetimin görünüşünü durumunu temel alarak değiştirin](#Visual)

- [Kaynaklar: renkler, stiller ve şablonlar oluşturun ve daha sonra yeniden kullanın](#Resources)

## <a name="Brushes"></a>Fırçalar: bir nesnenin görünümünü değiştirme
 Görünümünü değiştirmek istiyorsanız nesneye bir fırça uygulayın.

 **Kısa bir video izleyin:** ![yüklü Özellikler](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [fırçalar düzenleyicisini](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor)yapılandırma.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Bir nesne üzerinde yinelenen bir görüntüyü veya kalıbı boyama
 *Döşeme fırçası*kullanarak bir nesne üzerinde yinelenen bir görüntüyü veya kalıbı boyayın.

 Bir kutucuk fırçası oluşturmak için, bir *görüntü fırçası*, *Çizim Fırçası*veya *görsel fırça* kaynağı oluşturarak başlarsınız.

 Görüntü kullanarak bir görüntü fırçası oluşturun. Aşağıdaki çizimlerde, görüntü fırçası, görüntü fırçası döşeli ve görüntü fırçasının çevrilmiş olarak gösterildiği gösterilmektedir.

 ![](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31")![](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2")![](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png "38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")

 Yol veya şekil gibi bir vektör çizimi kullanarak bir çizim Fırçası oluşturun. Aşağıdaki çizimler çizim Fırçası, çizim Fırçası döşeli ve çizim fırçasını çevrilmiş olarak gösterir.

 ![](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5")![](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc")![](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png "15bf6021-620c-4490-9eae-086153d3f14f")

 Düğme gibi bir denetimden görsel fırça oluşturun. Aşağıdaki çizimlerde görsel fırça ve görsel fırça döşeli gösterilmektedir.

 ![](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227") ![](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")

 **Kısa bir video izleyin:** ![yüklü Özellikler](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [kutucuk fırçalarını](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes)yapılandırma.

## <a name="Styles"></a>Stiller ve şablonlar: denetimler arasında tutarlı bir görünüm oluşturma
 Bir denetimin görünümünü ve davranışını bir kez tasarlayabilir ve bu tasarımı farklı denetimlere uygulayabilir, böylece bunları ayrı ayrı tutmak zorunda kalmazsınız.

 **Bir stil kullanmanız gerekir mi?** : yalnızca varsayılan özellikleri (örneğin, bir düğmenin rengi) ayarlamak istiyorsanız, bir *Stil*kullanın. Bir stili uyguladıktan sonra bile bir denetimi değiştirebilirsiniz.

 **Bir şablon kullanmanız gerekir mi?** : bir denetimin yapısını değiştirmek istiyorsanız, bir *şablon*kullanın. Bir grafiği veya logoyu bir düğmeye dönüştürmeyi düşünün. Bir şablonu ona uyguladıktan sonra bir denetimi değiştiremezsiniz.

### <a name="create-a-template-or-style"></a>Şablon veya stil oluşturma
 Şablon oluşturmanın iki yolu vardır. Çalışma yüzeyinizdeki herhangi bir nesneyi bir denetime dönüştürebilir veya şablonunuzu varolan bir denetime dayandırdırabilirsiniz.

 Herhangi bir nesneyi bir denetim şablonuna dönüştürmek için, nesneyi seçin ve ardından **Araçlar** menüsünde **Denetim yap**' ı seçin.

 Şablonunuzu varolan bir denetime dayandırmak istiyorsanız çalışma yüzeyinde bir nesne seçin. Sonra, çalışma yüzeyinin üst kısmında, içerik haritası düğmesini seçin, **Şablonu Düzenle**' yi seçin ve ardından **bir kopyayı Düzenle** veya **boş oluştur**' u seçin.

 ![](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")

 Bir stil oluşturmak için, nesneyi seçin ve ardından **nesne** menüsünde **stili Düzenle**' yi seçin ve ardından **bir kopyayı Düzenle** veya **boş oluştur**' u seçin.

- Varsayılan stille veya denetimin şablonuyla başlamak için **bir kopyayı Düzenle** ' yi seçin.

- Sıfırdan başlamak için **boş oluştur** ' a tıklayın.

  **Geçerli öğeyi Düzenle** seçeneği yalnızca önceden oluşturduğunuz bir stili veya şablonu düzenlediğinizde görüntülenir. Hala varsayılan bir sistem şablonu kullanan bir denetim için görüntülenmez.

  **Stil kaynağı oluştur** iletişim kutusunda, daha sonra kullanabilmeniz için stili veya şablonu adlandırın ya da stili veya şablonu bu türün tüm denetimlerine uygulayabilirsiniz.

  ![](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")

> [!NOTE]
> Her denetim türü için stil veya şablon oluşturamazsınız. Bir denetim bunları desteklemiyorsa, içerik haritası düğmesi çalışma yüzeyi üzerinde görünmez.
>
> Ana belgenizin düzenlenme kapsamına dönmek için, **kapsamı geri döndür** ![ ](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4F20-aa66-a6f5b23eeb2b")' e tıklayın.
>
> ![](../designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")

 **Kısa bir video izleyin:** ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [Stil oluşturma](https://www.youtube.com/watch?v=W8YdXDPeKdc).

### <a name="apply-a-style-or-template-to-a-control"></a>Denetime stil veya şablon uygulama
 [Nesneler ve zaman çizelgesi](https://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57) panelinde bir nesneye sağ tıklayın, **Şablonu Düzenle**' yi ve ardından **kaynağı Uygula**' yı seçin.

 ![](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")

### <a name="restore-the-default-style-or-template-of-a-control"></a>Bir denetimin varsayılan stilini veya şablonunu geri yükleme
 Denetimi seçin ve [Özellikler](https://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57) panelinde **Stil** veya **şablon** özelliğini bulun. Ardından, **Gelişmiş Seçenekler** ![ ](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb")' e tıklayın ve ardından kısayol menüsünde **Sıfırla** ' ya tıklayın.

## <a name="Visual"></a>Görsel durumlar: bir denetimin görünüşünü durumunu temel alarak değiştirin
 Denetimlerin kullanıcı etkileşimlerine göre farklı görsel görünümleri olabilir. Örneğin, bir Kullanıcı üzerini tıklattığında veya bir animasyon çalıştırdığınızda bir düğmeyi yeşil hale getirebilirsiniz. Geçişleri kullanarak görsel durumlar arasındaki süreyi kısaltın veya uzatin.

 ![](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")

 **Kısa bir video izleyin:** ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [WPF denetimlerinizin durumunu yönetin](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="Resources"></a>Kaynaklar: renkler, stiller ve şablonlar oluşturun ve daha sonra yeniden kullanın
 Yalnızca projenizde bir şeyi bir kaynağa dönüştürebilirsiniz. Bir kaynak, yalnızca uygulamanızdaki farklı yerlerde yeniden kullanabileceğiniz bir nesnedir. Örneğin, bir kez renk oluşturabilir, bunu kaynak yapabilir ve daha sonra bu rengi çeşitli nesnelerde kullanabilirsiniz. Bu nesnelerin tümünün rengini değiştirmek için, yalnızca renk kaynağını değiştirmeniz yeterlidir.

 ![](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-CF66-46e0-B153-52a23cd744f7") ![](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")

 **Kısa bir video izleyin:** ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [kaynakları için kısa bir dokunma](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
