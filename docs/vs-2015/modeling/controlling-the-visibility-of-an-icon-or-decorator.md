---
title: Bir simgenin veya Dekorörün görünürlüğünü denetleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49cecff999e0155209ba58c20c0d623b15d63698
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667823"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Bir Simgenin veya Dekoratörün Görünürlüğünü Denetleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Dekoratör* , etki alanına özgü DILDE (DSL) bir şekil üzerinde görüntülenen bir simge veya metin satırıdır. Modelin özelliklerinin durumuna bağlı olarak dekoratörün görünmesini ve kaybolmasını sağlayabilirsiniz. Örneğin, bir kişiyi temsil eden bir şekil üzerinde, kişinin cinsiyetine, alt öğe sayısına ve buna bağlı olarak görünen farklı simgelere sahip olabilirsiniz.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Bir simgenin veya dekoratörün görünürlüğünü denetleme
 Aşağıdaki yordam bir şekli ve bir etki alanı sınıfıyla eşlemesini tanımlamış olduğunuzu varsayar. Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Bir simgenin veya metin dekoratörün görünürlüğünü denetlemek için

1. DSL tanımı diyagramında, görünmesini istediğiniz simgeleri veya metin dekoratlarını şekil sınıfına ekleyin.

   1. Şekil sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve gereken dekoratör türüne tıklayın.

   2. Dekoratör 'ın **Position** özelliğini ayarlayın. Birden çok dekoratör aynı konuma sahip olabilir. Örneğin, erkek ve kadın paylaşım için aynı konumda simgeler olabilir.

   3. Bir simge dekoratörü 'nin **varsayılan Icon** özelliğini ayarlayın.

2. DSL tanımı diyagramındaki şekil sınıfı ve alan sınıfı arasındaki gri çizgi olan diyagram öğesi haritasını seçin.

3. DSL ayrıntıları penceresindeki **dekoratör haritaları** sekmesinde bir dekoratör seçin. Örneğin, MaleDecorator.

4. **Görünürlük filtre** kutusunu işaretleyin.

5. Görünürlüğü denetlemek zorunda olan etki alanı özelliği hemen etki alanı sınıfında ise, **özelliği, filtre Için yolu** boş bırakın.

    Aksi takdirde, açılan menüye tıklayın ve özelliğin bulunduğu ilişkiye veya sınıfa gidin.

   - Bir hata raporunu önlemek için, gezinti aracında "*" ile işaretlenmiş bir ilişkide gezinmemelisiniz.

6. **Filter özelliğini** bir Domain özelliği olarak ayarlayın. Örneğin, cinsiyet.

7. **Görünürlük girişleri** listesinde, bu alan özelliğinin, dekoratörün görünür olması gereken değerlerini ekleyin. Örneğin, erkek.

8. Her simge için adımları yineleyin.

9. **Tüm şablonları dönüştürün**, derleyin ve çalıştırın ve bir test diyagramı açın.

10. Denetim özelliği değerini değiştirdiğinizde dekoratörler görünmeli ve kaybolur.

    Genellikle, görünürlüğün basit bir değer kümesinden daha karmaşık bir formül tarafından denetlenmesini istersiniz. Örneğin, bir simgenin belirli bir türdeki bağlantıların sayısına bağlı olması veya bir sayının belirli bir aralıkta olup olmamasına bağlı olması için. Bu durumda, aşağıdaki yordamı kullanın.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Bir formüle göre dekoratörün görünürlüğünü denetlemek için

1. Etki alanı sınıfına hesaplanmış bir etki alanı özelliği ekleyin. **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:

     **Igözatılabilen =** `False` **-Bu, özelliği kullanıcıdan gizler**

     **Tür =** `Calculated` **-Bu, değerini hesaplayan kodu sağlayacaksınız** .

     Örnek, **Dekoratorcontrol** **adı**

     **Tür**  =  `Boolean`

     Daha fazla bilgi için bkz. [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).

2. Yeni Özellik denetimini dekoratör görünürlüğünü yapın.

    1. Etki alanı sınıfından şekle gri çizgi olan diyagram öğesi haritasını seçin. **DSL ayrıntıları** penceresinde, **dekoratormap** sekmesini açın.

    2. **Görünürlük filtre** kutusunu işaretleyin.

    3. **Filter özelliğinde**, denetim özelliği **dekoratorcontrol**' u seçin.

    4. **Görünürlük girişleri**altında `True` girin.

3. Çözüm Gezgini araç çubuğunda **Tüm Şablonları Dönüştür** ' e tıklayın.

4. **Yapı** menüsünde **çözüm oluştur** ' a tıklayın.

5. Görüntülenen hata raporuna çift tıklayın: "*YourClass* , Getdekoratorcontrolvalue... için bir tanım içermiyor.

     Dsl\GeneratedCode\DomainClasses.cs. üzerinde metin Düzenleyicisi açılıyor Vurgulanan hatanın üstünde bir yöntem eklemenizi isteyen bir açıklama bulunur.

6. Eksik olan ad alanı, sınıf ve yöntemi unutmayın.  Örneğin, Company. FamilyTree. Person. Getdekoratorcontrolvalue ().

7. Ayrı bir kod dosyasında, eksik yöntemi içeren kısmi bir sınıf tanımı yazın. Örneğin:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Modeli program kodu ile özelleştirme hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Çözümü yeniden derleyin ve çalıştırın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Şekilleri ve bağlayıcıları tanımlama](../modeling/defining-shapes-and-connectors.md) [bir diyagram üzerinde arka plan görüntüsü ayarlama](../modeling/setting-a-background-image-on-a-diagram.md) [Program kodu](../modeling/navigating-and-updating-a-model-in-program-code.md) [yazma kodu, etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
