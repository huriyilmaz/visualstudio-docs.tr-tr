---
title: Dosya Depolamayı ve XML Serileştirmeyi Özelleştirme
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07592247e0afb870f3c4774c6f2023a6e8141cd1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542746"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Dosya Depolama ve XML Serileştirmeyi Özelleştirme

Kullanıcı, Visual Studio 'da alana özgü dilin (DSL) bir örneğini veya *modelini*kaydettiğinde, bir XML dosyası oluşturulur veya güncelleştirilir. Dosyayı depoda yeniden oluşturmak için dosya yeniden yüklenebilir.

DSL Gezgini 'nde **XML serileştirme davranışı** altındaki ayarları ayarlayarak serileştirme şemasını özelleştirebilirsiniz. Her etki alanı sınıfı, özelliği ve ilişkisi için **XML serileştirme davranışı** altında bir düğüm vardır. İlişkiler, kaynak sınıflarının altında bulunur. Ayrıca şekil, bağlayıcı ve diyagram sınıflarına karşılık gelen düğümler de vardır.

Ayrıca, daha gelişmiş özelleştirme için program kodu yazabilirsiniz.

> [!NOTE]
> Modeli belirli bir biçimde kaydetmek istiyorsanız ancak bu formdan yeniden yüklemeniz gerekmiyorsa, özel bir serileştirme düzeni yerine modelden çıkış oluşturmak için metin şablonları kullanmayı düşünün. Daha fazla bilgi için bkz. [etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Model ve diyagram dosyaları

Her model genellikle iki dosyada kaydedilir:

- Model dosyası **Model1. mydsl**gibi bir ada sahiptir. Model öğelerini ve ilişkilerini ve bunların özelliklerini depolar. **. Mydsl** gibi dosya UZANTıSı, dsl tanımındaki **Düzenleyici** düğümünün **FileExtension** özelliği tarafından belirlenir.

- Diyagram dosyası **Model1. mydsl. Diagram**gibi bir ada sahiptir. Şekilleri, bağlayıcıları ve bunların konumlarını, renklerini, satır kalınlıklarda ve diyagramın görünümünün diğer ayrıntılarını depolar. Kullanıcı bir **. Diagram** dosyasını silerse, modeldeki önemli bilgiler kaybedilmez. Yalnızca diyagramın yerleşimi kaybolur. Model dosyası açıldığında, varsayılan bir şekil ve bağlayıcılar kümesi oluşturulur.

### <a name="to-change-the-file-extension-of-a-dsl"></a>DSL dosya uzantısını değiştirmek için

1. DSL tanımını açın. DSL Gezgini ' nde düzenleyici düğümüne tıklayın.

2. Özellikler penceresi, **FileExtension** özelliğini düzenleyin. Dosya adı uzantısının ilk "." ni eklemeyin.

3. Çözüm Gezgini, **Dslpackage\projectıtemtemplates**içindeki iki öğe şablonu dosyasının adını değiştirin. Bu dosyalar şu biçimi izleyen adlara sahiptir:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Varsayılan serileştirme düzeni

Bu konuyla ilgili bir örnek oluşturmak için aşağıdaki DSL tanımı kullanılmıştır.

![DSL tanımı diyagramı &#45; aile ağacı modeli](../modeling/media/familyt_person.png)

Bu DSL, ekranda aşağıdaki görünüme sahip bir model oluşturmak için kullanılmıştır.

![Aile ağacı diyagramı, araç kutusu ve gezgin](../modeling/media/familyt_instance.png)

Bu model kaydedildi ve sonra XML metin düzenleyicisinde yeniden açıldı:

```xml
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>
```

Serileştirilmiş model hakkında aşağıdaki noktalara dikkat edin:

- Her XML düğümü, bir etki alanı sınıf adı ile aynı bir ada sahiptir, ancak ilk harf küçük harfle yazılmalıdır. Örneğin `familyTreeModel` ve `person`.

- Ad ve Doğum yılı gibi etki alanı özellikleri, XML düğümlerinde öznitelikler olarak serileştirilir. Yeniden, özellik adının ilk karakteri küçük harfe dönüştürülür.

- Her ilişki, ilişkinin kaynak ucunun içinde iç içe yerleştirilmiş bir XML düğümü olarak serileştirilir. Düğüm, kaynak rol özelliğiyle aynı ada sahip, ancak küçük bir başlangıç karakteriyle aynı.

     Örneğin, DSL tanımında, **kişiler** adlı bir rol **FamilyTree** sınıfında kaynaklıdır.  XML 'de, bu düğüm `people` içinde iç içe yerleştirilmiş adlı düğüm tarafından temsil edilir `familyTreeModel` .

- Her katıştırma ilişkisinin hedef sonu, ilişki altında iç içe geçmiş bir düğüm olarak serileştirilir. Örneğin, `people` düğüm birkaç `person` düğüm içerir.

- Her başvuru ilişkisinin hedef sonu, hedef öğeye bir başvuruyu kodlayan bir *bilinen ad*olarak serileştirilir.

     Örneğin, bir düğüm altında bir `person` `children` ilişki olabilir. Bu düğüm aşağıdaki gibi bilinen adlar içerir:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Bilinen adları anlama

Takma adlar, model ve diyagram dosyalarının farklı parçaları arasındaki çapraz başvuruları temsil etmek için kullanılır. Ayrıca `.diagram` dosya içinde model dosyasındaki düğümlere başvurmak için kullanılır. İki bilinen ad biçimi vardır:

- *Kimlik takma adları* hedef öğenin GUID 'si. Örneğin:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- *Nitelenmiş anahtar takma adları* , bilinen bir etki alanı özelliği olan ad anahtarı adı ile hedef öğeyi belirler. Hedef öğenin bilinen adı, üst öğesinin adının sonuna eklenir ve ekleme ilişkileri ağacı.

     Aşağıdaki örnekler, Song adlı bir etki alanı sınıfına katıştırma ilişkisi bulunan, albüm adlı bir etki alanı sınıfı olan bir DSL 'den alınmıştır:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Hedef sınıfın, **bilinen** bir etki alanı özelliği varsa ve bu seçenek, `true` **XML serileştirme davranışı**olarak ayarlandığında, tam anahtar takma adları kullanılacaktır. Örnekte bu seçenek, "albüm" ve "Song" etki alanı sınıflarında "title" adlı etki alanı özellikleri için ayarlanır.

Nitelikli anahtar adları, KIMLIK adlarıyla daha kolay okunabilir. Model dosyalarınızın XML 'sini kişiler tarafından okunacak şekilde düşünüyorsanız, tam anahtar adları kullanmayı göz önünde bulundurun. Ancak, kullanıcının aynı ad anahtarına sahip olacak birden fazla öğe ayarlaması mümkündür. Yinelenen anahtarlar dosyanın doğru şekilde yeniden çalışmamasına neden olabilir. Bu nedenle, tam anahtar takma adları kullanılarak başvurulan bir etki alanı sınıfı tanımlarsanız, kullanıcının yinelenen adlar içeren bir dosyayı kaydetmesini engelleyen yollar göz önünde bulundurmanız gerekir.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Bir etki alanı sınıfını KIMLIK adlarıyla başvurulacak şekilde ayarlamak için

1. **Is Moniker Key** `false` Sınıfın ve temel sınıflarının her etki alanı özelliği Için bilinen ad anahtarı olduğundan emin olun.

    1. DSL Gezgini 'nde **XML serileştirme Behavior\Class Data \\ \<the domain class> \element Data**öğesini genişletin.

    2. Her etki alanı özelliği için **bilinen ad anahtarının** olduğunu doğrulayın `false` .

    3. Etki alanı sınıfında bir temel sınıf varsa, yordamı bu sınıfta tekrarlayın.

2. Alan sınıfı için **seri hale getirme kimliği** ayarlayın  =  `true` .

     Bu özellik, **XML serileştirme davranışı**altında bulunabilir.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Bir etki alanı sınıfını tam anahtar adlarıyla başvurulacak şekilde ayarlamak için

- Set, var olan bir etki alanı sınıfının bir Domain özelliği için **bilinen ad anahtarıdır** . Özelliğin türü olmalıdır `string` .

    1. DSL Gezgini 'nde **XML serileştirme Behavior\Class Data \\ \<the domain class> \element Data**öğesini genişletin ve ardından domain özelliğini seçin.

    2. Özellikler penceresi, için **bilinen ad anahtarı** ' nı belirleyin `true` .

- \- veya

     **Adlandırılmış alan sınıfı** aracını kullanarak yeni bir etki alanı sınıfı oluşturun.

     Bu araç, Name adlı bir etki alanı özelliğine sahip yeni bir sınıf oluşturur. **Öğesi öğesinin adı** ve bu etki alanı özelliğinin **bilinen ad anahtarı** özellikleri olarak başlatılır `true` .

- \- veya

     Etki alanı sınıfından, bilinen ad anahtarı özelliğine sahip başka bir sınıfa devralma ilişkisi oluşturun.

### <a name="avoid-duplicate-monikers"></a>Yinelenen bilinen adların olmaması

Nitelikli anahtar adlar kullanırsanız, bir kullanıcının modelindeki iki öğenin anahtar özelliğinde aynı değere sahip olabilme olasılığı vardır. Örneğin, DSL 'niz bir özellik adına sahip bir sınıf kişiye sahipse, Kullanıcı iki öğenin adını aynı olacak şekilde ayarlayabilir. Model dosyaya kaydedibilse de, doğru şekilde yeniden yüklenemez.

Bu durumdan kaçınmaya yardımcı olacak birkaç yöntem vardır:

- **Is Element Name**  =  `true` Anahtar alanı özelliği için bir öğe adı belirleyin. DSL tanımı diyagramında etki alanı özelliğini seçin ve Özellikler penceresi değeri ayarlayın.

     Kullanıcı, sınıfın yeni bir örneğini oluşturduğunda, bu değer etki alanı özelliğine otomatik olarak farklı bir değer atanmasına neden olur. Varsayılan davranış, sınıf adının sonuna bir sayı ekler. Bu, kullanıcının adı yinelenen olarak değiştirmesini engellemez, ancak kullanıcı modeli kaydetmeden önce değeri ayarlamadan bu durumda yardımcı olur.

- DSL için doğrulamayı etkinleştirin. DSL Gezgini ' nde, Editor\Validation ' ı seçin ve **kullanımları...** özelliklerini olarak ayarlayın `true` .

     Belirsizlikleri için denetleyen otomatik olarak oluşturulan bir doğrulama yöntemi vardır. Yöntemi `Load` doğrulama kategorisinde bulunur. Bu, kullanıcının dosyayı yeniden açmak mümkün olmadığını belirten bir uyarı olacaktır.

     Daha fazla bilgi için bkz. [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Bilinen ad yolları ve niteleyicileri

Nitelenmiş anahtar bilinen adı, bilinen ad anahtarıyla sonlanır ve ekleme ağacındaki üst öğesinin bilinen adıyla birlikte eklenir. Örneğin, bir albümün bilinen adı:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Sonra bu albümdeki şarkıların biri şu şekilde olabilir:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Ancak, bunun yerine Albümler KIMLIK olarak başvuruluyorsa, bilinen adlar aşağıdaki gibi olacaktır:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Bir GUID benzersiz olduğu için, kendisinin üst öğesinin bilinen adının hiçbir şekilde önüne alınmadığından emin olun.

Belirli bir etki alanı özelliğinin her zaman bir model içinde benzersiz bir değere sahip olacağını biliyorsanız, bu özellik için bir **bilinen ad niteleyicisi** belirleyebilirsiniz `true` . Bu, üst öğenin bilinen adını kullanmadan bir niteleyici olarak kullanılmasına neden olur. Örneğin, hem **bilinen ad niteleyicisi** hem de albüm sınıfının title Domain özelliği için **bilinen ad anahtarı** ' nı ayarlarsanız, modelin adı veya tanımlayıcısı, albüm ve katıştırılmış alt öğeleri için takma adlar içinde kullanılmaz:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>XML yapısını özelleştirme

Aşağıdaki özelleştirmeleri yapmak için, DSL Gezgini 'ndeki **XML serileştirme davranışı** düğümünü genişletin. Bir etki alanı sınıfı altında, bu sınıfta kaynak olan özelliklerin ve ilişkilerin listesini görmek için öğe veri düğümünü genişletin. Bir ilişki seçin ve Özellikler penceresi seçeneklerini ayarlayın.

- Kaynak rol düğümünü atlamak için, yalnızca hedef öğelerin listesini bırakarak, **atlayın öğesini** true olarak ayarlayın. Kaynak ve hedef sınıflar arasında birden fazla ilişki varsa bu seçeneği belirtmemelisiniz.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- Hedef düğümleri ilişki örneklerini temsil eden düğümlere katıştırmak için **tam form kullan** ' a ayarlayın. Bu seçenek, bir etki alanı ilişkisine etki alanı özellikleri eklediğinizde otomatik olarak ayarlanır.

    ```xml
    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>
    ```

- **Temsili**  =  **öğesini** , öznitelik değeri olarak değil bir öğe olarak kaydedilmiş bir etki alanı özelliğine sahip olacak şekilde ayarlayın.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Özniteliklerin ve ilişkilerin serileştirildiği sırayı değiştirmek için, öğe verileri altındaki bir öğeye sağ tıklayın ve **Yukarı taşı** veya **aşağı taşı** menü komutlarını kullanın.

## <a name="major-customization-using-program-code"></a>Program kodunu kullanarak ana özelleştirme

Tüm serileştirme algoritmalarının parçalarını veya tümünü değiştirebilirsiniz.

**Dsl\generated Code\Serializer.cs** ve **SerializationHelper.cs**içindeki kodu inceetmenizi öneririz.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Belirli bir sınıfın serileştirmesini özelleştirmek için

1. Küme, **XML serileştirme davranışı**altındaki bu sınıfın düğümünde **özel** olarak ayarlanır.

2. Tüm şablonları dönüştürün, çözümü derleyin ve ortaya çıkan derleme hatalarını araştırın. Her hatanın yakınında bulunan açıklamalar, hangi kodun sağlamanız gerektiğini açıklar.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Tüm model için kendi serileştirmesini sağlamak için

1. Dsl\GeneratedCode\SerializationHelper.cs içindeki yöntemleri geçersiz kıl

## <a name="options-in-xml-serialization-behavior"></a>XML serileştirme davranışlarındaki seçenekler

DSL Gezgini 'nde, XML serileştirme davranışı düğümü her bir etki alanı sınıfı, ilişki, şekil, bağlayıcı ve Diyagram sınıfı için bir alt düğüm içerir. Bu düğümlerin her biri, ilgili öğede kaynak olarak bulunan özelliklerin ve ilişkilerin bir listesidir. İlişkiler hem kendi hem de kaynak sınıflarının altında temsil edilir.

Aşağıdaki tabloda DSL tanımının bu bölümünde ayarlayabileceğiniz seçenekler özetlenmektedir. Her durumda DSL Gezgini ' nde bir öğe seçin ve Özellikler penceresi seçenekleri ayarlayın.

### <a name="xml-class-data"></a>XML sınıfı verileri

Bu öğeler, **XML serileştirme Behavior\Class verileri**altında DSL Gezgini 'nde bulunur.

|Özellik|Açıklama|
|-|-|
|Özel öğe şemasına sahip|True ise, alan sınıfının özel bir öğe şemasına sahip olduğunu belirtir|
|Özel|Bu etki alanı sınıfı için kendi serileştirme ve seri durumdan çıkarma kodunuzu yazmak istiyorsanız bunu **true** olarak ayarlayın.<br /><br /> Çözümü oluşturun ve ayrıntılı yönergeleri bulmaya yönelik hataları araştırın.|
|Alan sınıfı|Bu sınıf veri düğümünün geçerli olduğu etki alanı sınıfı. Salt okunur.|
|Öğe Adı|Bu sınıfın öğeleri için XML düğümü adı. Varsayılan değer, etki alanı sınıf adının küçük bir sürümüdür.|
|Bilinen ad öznitelik adı|Başvuruyu içermesi için bilinen ad öğelerinde kullanılan özniteliğin adı. Boşsa, anahtar özelliğin veya kimliğin adı kullanılır.<br /><br /> Bu örnekte, "ad" dır:  `<personMoniker name="/Mike Nash"/>`|
|Bilinen ad öğe adı|Bu sınıfın öğelerine başvuran bilinen adlar için kullanılan XML öğesinin adı.<br /><br /> Varsayılan değer, "bilinen ad" ile düzeltilen sınıf adının küçük harfli bir sürümüdür. Örneğin, `personMoniker`.|
|Bilinen ad türü adı|Bu sınıfın öğelerine ait bilinen adlar için oluşturulan xsd türünün adı. XSD, **Dsl\generated Code \\ \* Schema. xsd** ' dir|
|Seri hale getirme kimliği|True ise, öğe GUID 'SI dosyaya dahil edilir. Bu, **bilinen** bir özellik varsa ve bu sınıf için başvuru ilişkilerini tanımlarsa, bu doğru olmalıdır.|
|Tür adı|Belirtilen etki alanı sınıfından xsd içinde oluşturulan XML türünün adı.|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar|

### <a name="xml-property-data"></a>Xml özelliği verileri

XML özellik düğümleri sınıf düğümleri altında bulunur.

|Özellik|Açıklama|
|-|-|
|Domain özelliği|XML serileştirme yapılandırması verilerinin geçerli olduğu özellik. Salt okunur.|
|Bilinen ad anahtarı|True ise, özelliği bu alan sınıfının örneklerine başvuran takma adlar oluşturmak için anahtar olarak kullanılır.|
|Bilinen ad niteleyicisi|True ise özellik, bilinen adlar içinde niteleyiciyi oluşturmak için kullanılır. Yanlış ise ve bu etki alanı sınıfı için SerializeId true değilse, adlar ekleme ağacındaki üst öğenin bilinen adı ile nitelenir.|
|İmle|Eğer özniteliği ise, özelliği bir XML özniteliği olarak serileştirilir; Öğesi ise, öğe olarak serileştirilir; Yoksayma ise serileştirilmez.|
|Xml adı|XML özniteliği veya özelliği temsil eden öğe için kullanılan ad. Bu, varsayılan olarak, etki alanı özelliği adının küçük bir sürümüdür.|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar|

### <a name="xml-role-data"></a>XML rolü verileri

Rol veri düğümleri kaynak sınıfı düğümleri altında bulunur.

|Özellik|Açıklama|
|-|-|
|Özel bilinen adı vardır|Bu ilişkiye çapraz geçiş yapan takma adların oluşturulması ve çözümlenmesi için kendi kodunuzu sağlamak istiyorsanız bunu true olarak ayarlayın.<br /><br /> Ayrıntılı yönergeler için çözümü oluşturun ve ardından hata iletilerine çift tıklayın.|
|Etki alanı Ilişkisi|Bu seçeneklerin uygulandığı ilişkiyi belirtir. Salt okunur.|
|Öğeyi atla|True ise, kaynak rolüne karşılık gelen XML düğümü şemadan çıkarılır.<br /><br /> Kaynak ve hedef sınıflar arasında birden fazla ilişki varsa, bu rol düğümü iki ilişkiye ait bağlantılar arasında ayrım yapar. Bu nedenle bu seçeneği bu durumda ayarlamanıza tavsiye ederiz.|
|Rol öğesi adı|Kaynak rolünden türetilmiş XML öğesinin adını belirtir. Varsayılan değer rol özelliği adıdır.|
|Tam form kullan|True ise, her hedef öğe veya bilinen ad ilişkiyi temsil eden bir XML düğümü içine alınmıştır. İlişkinin kendi etki alanı özellikleri varsa, bu true olarak ayarlanmalıdır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
