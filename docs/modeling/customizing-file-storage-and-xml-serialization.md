---
title: Dosya Depolamayı ve XML Serileştirmeyi Özelleştirme
description: Etki alanına özgü bir dilin (DSL) örneğini veya modelini kaydediyorsanız oluşturulan veya güncelleştirilen XML dosyası hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: cf3f80c51866f278f4cf9a72876963d60ab17e4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061317"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Dosya Depolama ve XML Serileştirmeyi Özelleştirme

Kullanıcı etki alanına özgü bir dilin (DSL) bir örneğini veya *modelini* Visual Studio XML dosyası oluşturulur veya güncelleştirilir. Modeli Store'da yeniden oluşturmak için dosya yeniden yüklenebilir.

DSL Gezgini'nde Xml Serileştirme Davranışı altındaki ayarları **ayarlayarak serileştirme** düzenini özelleştirebilirsiniz. Her etki alanı sınıfı, **özelliği ve ilişkisi için Xml** Serileştirme Davranışı altında bir düğüm vardır. İlişkiler, kaynak sınıflarının altında bulunur. Şekil, bağlayıcı ve diyagram sınıflarına karşılık gelen düğümler de vardır.

Daha gelişmiş özelleştirme için program kodu da yazabilirsiniz.

> [!NOTE]
> Modeli belirli bir biçimde kaydetmek istiyor ancak bu formda yeniden yüklemeniz gerek yoksa, özel serileştirme düzeni yerine modelden çıkış oluşturmak için metin şablonlarını kullanmayı göz önünde bulundurabilirsiniz. Daha fazla bilgi için [bkz. Domain-Specific Dilinden Kod Oluşturma.](../modeling/generating-code-from-a-domain-specific-language.md)

## <a name="model-and-diagram-files"></a>Model ve Diyagram Dosyaları

Her model genellikle iki dosyada kaydedilir:

- Model dosyası, **Model1.mydsl gibi bir ad içerir.** Model öğelerini, ilişkilerini ve özelliklerini depolar. **.mydsl** gibi dosya uzantısı DSL Tanımı'nın Düzenleyici düğümünün **FileExtension** özelliği tarafından belirlenir. 

- Diyagram dosyasının adı **Model1.mydsl.diagram gibi bir ad içerir.** Şekilleri, bağlayıcıları ve konumlarını, renklerini, çizgi kalınlıklarını ve diyagramın görünümünün diğer ayrıntılarını depolar. Kullanıcı bir **.diagram dosyasını silerse** modelde temel bilgiler kaybolur. Yalnızca diyagramın düzeni kaybolur. Model dosyası açıldığında, varsayılan bir şekil ve bağlayıcı kümesi oluşturulur.

### <a name="to-change-the-file-extension-of-a-dsl"></a>DSL'nin dosya uzantısını değiştirmek için

1. DSL Tanımını açın. DSL Gezgini'nde Düzenleyici düğümüne tıklayın.

2. Dosya Özellikler penceresi **FileExtension özelliğini** düzenleyin. Dosya adı uzantısının ilk "." harfini dahil değildir.

3. Bu Çözüm Gezgini **DslPackage\ProjectItemTemplates** konumundaki iki öğeli şablon dosyalarının adını değiştirebilirsiniz. Bu dosyaların adları şu biçimdedir:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Varsayılan Serileştirme Şeması

Bu konuya bir örnek oluşturmak için aşağıdaki DSL Tanımı kullanılmıştır.

![DSL Tanımı diyagramı &#45; ağaç modeli](../modeling/media/familyt_person.png)

Bu DSL, ekranda aşağıdaki görünüme sahip bir model oluşturmak için kullanılmıştır.

![Aile ağacı diyagramı, araç kutusu ve gezgin](../modeling/media/familyt_instance.png)

Bu model kaydedildi ve XML metin düzenleyicisinde yeniden açıldı:

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

Serileştirilmiş model hakkında aşağıdaki noktalara dikkatin:

- Her XML düğümünün bir etki alanı sınıf adıyla aynı olan bir adı vardır, ancak ilk harfin küçük harf olması gerekir. Örneğin `familyTreeModel` ve `person`.

- Name ve BirthYear gibi etki alanı özellikleri XML düğümlerde öznitelik olarak seri hale getirilecek. Burada da özellik adının ilk karakteri küçük harfe dönüştürülür.

- Her ilişki, ilişkinin kaynak ucunda iç içe geçmiş bir XML düğümü olarak seri hale getirilir. Düğüm, kaynak rol özelliğiyle aynı adı içerir, ancak küçük harfli bir başlangıç karakteri içerir.

     Örneğin DSL Tanımında People adlı bir rol **FamilyTree** sınıfından gelir.   XML'de bu, düğümün içinde iç içe geçmiş `people` adlı düğümle `familyTreeModel` temsil edilen.

- Her ekleme ilişkisinin hedef sonu, ilişki altında iç içe geçmiş bir düğüm olarak seri hale getirilecek. Örneğin, düğüm `people` birkaç düğüm `person` içerir.

- Her başvuru ilişkisinin hedef sonu, hedef *öğeye* bir başvuru kodlayan bilinen ad olarak seri hale getirildiği.

     Örneğin, bir `person` düğüm altında bir ilişki `children` olabilir. Bu düğüm, aşağıdakiler gibi bilinen adlar içerir:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Bilinen Adlar'i anlama

Bilinen adlar, modelin farklı bölümleri ve diyagram dosyaları arasındaki çapraz başvuruları temsil etmek için kullanılır. Bunlar, model `.diagram` dosyasındaki düğümlere başvurmak için dosyasında da kullanılır. İki bilinen ad formu vardır:

- *Kimlik bilinen adlar* hedef öğenin GUID'ini tırnak içine alın. Örnek:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- *Tam anahtar bilinen adları,* hedef öğeyi bilinen anahtar olarak adlandırılan belirlenmiş bir etki alanı özelliğinin değerine göre belirtir. Hedef öğenin bilinen adı, ekleme ilişkileri ağacında üst öğesinin bilinen adı tarafından önek olarak önek olarak kullanılır.

     Aşağıdaki örnekler, Song adlı bir etki alanı sınıfına ekleme ilişkisine sahip olan Venes adlı bir etki alanı sınıfının olduğu DSL'den alınarak verilmiştir:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Hedef sınıfın Xml Serileştirme Davranışı'nde Bilinen Anahtar'dır seçeneğinin ayarildiği bir etki alanı özelliği varsa, tam anahtar bilinen adları  `true` **kullanılır.** Örnekte, bu seçenek "Şarkı" ve "Şarkı" etki alanı sınıflarında "Başlık" adlı etki alanı özellikleri için ayarlanır.

Tam anahtar bilinen adlarını okumak, kimlik bilinen adlarına göre daha kolaydır. Model dosyalarınızın XML'inin kişiler tarafından okunma amacına sahipse, tam anahtar bilinen adlarını kullanmayı göz önünde bulundurabilirsiniz. Ancak, kullanıcının aynı bilinen anahtara sahip olmak için birden fazla öğe ayarlaması mümkündür. Yinelenen anahtarlar, dosyanın doğru şekilde yeniden yüklenemama neden olabilir. Bu nedenle, tam anahtar bilinen adları kullanılarak başvurulan bir etki alanı sınıfı tanımlarsanız, kullanıcının yinelenen bilinen adlara sahip bir dosyayı kaydetmesini önlemenin yollarını göz önünde bulundurabilirsiniz.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Kimlik bilinen adları tarafından başvurulan bir etki alanı sınıfı ayarlamak için

1. Is **Moniker Key 'in sınıfındaki** `false` her etki alanı özelliği ve onun temel sınıfları için olduğundan emin olun.

    1. DSL Gezgini'nde **Xml Serileştirme Davranışı\Sınıf Verileri \\ \<the domain class> \Öğe Verileri'ni genişletin.**

    2. Is **Moniker Key 'in her** etki alanı `false` özelliği için olduğunu doğrulayın.

    3. Etki alanı sınıfının bir temel sınıfı varsa, yordamı bu sınıfta yineler.

2. Etki **alanı sınıfı için Serialize**  =  `true` Id'i ayarlayın.

     Bu özellik Xml Serileştirme Davranışı **altında bulunabilir.**

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Tam anahtar bilinen adları tarafından başvurulecek bir etki alanı sınıfı ayarlamak için

- Var olan bir etki alanı sınıfının bir etki alanı özelliği için Is **Moniker Key** olarak ayarlayın. Özelliğin türü türünde olması `string` gerekir.

    1. DSL Gezgini'nde **Xml Serileştirme Davranışı\Sınıf Verileri \\ \<the domain class> \Öğe Verileri'ni genişletin** ve ardından etki alanı özelliğini seçin.

    2. Aşağıdaki Özellikler penceresi, **Is Moniker Key (Bilinen AnahtarDır) olarak** `true` ayarlayın.

- \- veya -

     Adlandırılmış Etki Alanı Sınıfı aracını kullanarak yeni **bir etki alanı sınıfı** oluşturun.

     Bu araç, Name adlı bir etki alanı özelliğine sahip yeni bir sınıf oluşturur. Bu **etki alanı özelliğinin** **Is Öğesi Adı** ve Is Bilinen Anahtarı özellikleri olarak `true` başlatılır.

- \- veya -

     Etki alanı sınıfından bilinen anahtar özelliğine sahip başka bir sınıfa devralma ilişkisi oluşturun.

### <a name="avoid-duplicate-monikers"></a>Yinelenen Bilinen Adlardan Kaçının

Tam anahtar bilinen adlarını kullanırsanız, bir kullanıcı modelinde iki öğenin anahtar özelliğinde aynı değere sahip olması mümkündür. Örneğin, DSL'niz Name özelliğine sahip bir Kişi sınıfına sahipse, kullanıcı iki öğenin Adlarını aynı olacak şekilde ayarlayabilirsiniz. Model dosyaya kaydedilebilir ancak doğru şekilde yeniden yüklenemedi.

Bu durumdan kaçınmaya yardımcı olan çeşitli yöntemler vardır:

- Anahtar **etki alanı özelliği için** Is Öğe Adı olarak  =  `true` ayarlayın. DSL Tanımı diyagramında etki alanı özelliğini seçin ve ardından etki alanı Özellikler penceresi.

     Kullanıcı sınıfının yeni bir örneğini oluşturduğunda, bu değer etki alanı özelliğine otomatik olarak farklı bir değer atanma neden olur. Varsayılan davranış, sınıf adının sonuna bir sayı ekler. Bu, kullanıcının adı yinelenen olarak değiştirmesini engellemez, ancak kullanıcı modeli kaydetmeden önce değeri ayarlamazsa yardımcı olur.

- DSL için doğrulamayı etkinleştirin. DSL Gezgini'nde Düzenleyici\Doğrulama'ya tıklayın ve **Uses... özelliklerini** olarak `true` ayarlayın.

     Belirsizlikleri kontrol eder ve otomatik olarak oluşturulan bir doğrulama yöntemi vardır. yöntemi doğrulama `Load` kategorisindedir. Bu, kullanıcının dosyayı yeniden açmanın mümkün olmadığının uyarılmalarını sağlar.

     Daha fazla bilgi için, [bkz. Validation in a Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Bilinen Yollar ve Niteleyiciler

Tam anahtar bilinen adı, bilinen anahtar ile biter ve ekleme ağacında üst bilinen adı ile ön ekini ekler. Örneğin, Bir Yer'in bilinen adı şu ise:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Ardından Bu Müzik'te yer alan Songs'lardan biri şöyle olabilir:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Ancak, Bunun yerine Kimlik'e Id ile başvurulsa, bilinen adlar aşağıdaki gibi olur:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Guid benzersiz olduğundan, hiçbir zaman üst öğenin bilinen adı tarafından önek olarak kabul edilmildiğine dikkat edin.

Belirli bir etki alanı özelliğinin model içinde her zaman benzersiz bir değere sahip olduğunu biliyorsanız, bu özellik için **Is Moniker Niteleyicisi'ni** `true` olarak ayarlayın. Bu, üst öğenin bilinen adı kullanılmadan niteleyici olarak kullanılmaya neden olur. Örneğin, Sınıf Sınıfı'nın Title etki alanı özelliği için hem **Is Moniker Niteleyicisi** hem de Is **Moniker Key'i** ayarsanız, modelin adı veya tanımlayıcısı, Yalıtıcı adlarında ve ekli çocuklarında kullanılmaz:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>XML yapısını özelleştirme

Aşağıdaki özelleştirmeleri yapmak için DSL Gezgini'nde **Xml Serileştirme Davranışı** düğümünü genişletin. Bir etki alanı sınıfının altında, bu sınıfta kaynak olarak bulunan özelliklerin ve ilişkilerin listesini görmek için Öğe Verileri düğümünü genişletin. Bir ilişki seçin ve bu ilişkinin seçeneklerini Özellikler penceresi.

- Kaynak **rol düğümünü** atlar ve yalnızca hedef öğelerin listesini bırakarak Öğe Atla öğesini true olarak ayarlayın. Kaynak ve hedef sınıflar arasında birden fazla ilişki varsa bu seçeneği ayarlamamanız gerekir.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- Hedef **düğümleri ilişki örneklerini** temsil eden düğümlere eklemek için Tam Formu Kullan'ı ayarlayın. Bu seçenek, bir etki alanı ilişkisine etki alanı özellikleri eklerken otomatik olarak ayarlanır.

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

- Temsil   =  **Öğesi'nin** bir etki alanı özelliğinin öznitelik değeri olarak değil öğe olarak kaydedilmiş olarak ayarlanmıştır.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Özniteliklerin ve ilişkilerin seri hale getirme sıralarını değiştirmek için Öğe Verileri'nin altındaki bir öğeye sağ tıklayın ve Yukarı Taşı **veya** Aşağı Taşı **menü** komutlarını kullanın.

## <a name="major-customization-using-program-code"></a>Program kodunu kullanarak büyük özelleştirme

Serileştirme algoritmalarının parçalarını veya hepsini değiştirebilirsiniz.

**Dsl\Generated Code\Serializer.cs ve SerializationHelper.cs** içinde kodu **incelemenizi öneririz.**

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Belirli bir sınıfın serileştirmeyi özelleştirmek için

1. Bu **sınıfın düğümünde** Xml Serileştirme Davranışı altında Özel **olarak ayarlayın.**

2. Tüm Şablonları Dönüştür, çözümü derle ve sonuçta ortaya çıkan derleme hatalarını araştır. Her hataya yakın yorumlar hangi kodu sağlamanız gerektir olduğunu açıklar.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Modelin tamamı için kendi serileştirmenizi sağlamak için

1. Dsl\GeneratedCode\SerializationHelper.cs içinde geçersiz kılma yöntemleri

## <a name="options-in-xml-serialization-behavior"></a>Xml Serileştirme Davranışı seçenekleri

DSL Gezgini'nde Xml Serileştirme Davranışı düğümü her etki alanı sınıfı, ilişki, şekil, bağlayıcı ve diyagram sınıfı için bir alt düğüm içerir. Bu düğümlerin her biri altında, bu öğede kaynak olarak bulunan özelliklerin ve ilişkilerin listesi yer almaktadır. İlişkiler hem kendi sağlarında hem de kaynak sınıflarında temsil edildi.

Aşağıdaki tabloda DSL Tanımının bu bölümünde ayarlayabilirsiniz seçenekler özetlenmiştir. Her durumda DSL Gezgini'nde bir öğe seçin ve Özellikler penceresi.

### <a name="xml-class-data"></a>Xml Sınıfı verileri

Bu öğeler DSL Gezgini'nde **Xml Serileştirme Davranışı\Sınıf Verileri altında bulunur.**

|Özellik|Açıklama|
|-|-|
|Özel Öğe Şemasına Sahip|True ise, etki alanı sınıfının özel bir öğe şemasına sahip olduğunu gösterir|
|Özeldir|Bu etki alanı sınıfı için kendi serileştirme ve seri durumdan başlatma kodunuzu yazmak için bunu **True** olarak ayarlayın.<br /><br /> Çözümü derleme ve ayrıntılı yönergeleri bulmak için hataları araştırma.|
|Etki Alanı Sınıfı|Bu sınıf veri düğümünün uygulandığı etki alanı sınıfı. Salt okunur.|
|Öğe Adı|Bu sınıfın öğeleri için Xml düğümü adı. Varsayılan değer, etki alanı sınıf adının küçük harfli bir sürümüdür.|
|Bilinen Ad Öznitelik Adı|Başvuru içeren bilinen ad öğelerinde kullanılan özniteliğin adı. Boşsa anahtar özelliğinin veya kimliğinin adı kullanılır.<br /><br /> Bu örnekte "name" şeklindedir:  `<personMoniker name="/Mike Nash"/>`|
|Bilinen Öğe Adı|Bu sınıfın öğelerine başvuran bilinen adlar için kullanılan xml öğesinin adı.<br /><br /> Varsayılan değer, sınıf adının "Bilinen Ad" ile son ekli küçük harfli bir sürümüdür. Örneğin, `personMoniker`.|
|Bilinen Ad Türü Adı|Bu sınıfın öğelerine bilinen adlar için oluşturulan xsd türünün adı. XSD **Dsl\Generated Code \\ \* Schema.xsd konumundadır**|
|Seri Hale Getirme Kimliği|True ise, öğe GUID'si dosyaya dahil edilir. Is **Moniker Key** olarak işaretlenen bir özellik yoksa ve DSL bu sınıfa başvuru ilişkilerini tanımıyorsa bu doğru olması gerekir.|
|Tür Adı|Belirlenen etki alanı sınıfından xsd'de oluşturulan xml türünün adı.|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar|

### <a name="xml-property-data"></a>Xml Özellik Verileri

Xml Özellik düğümleri, sınıf düğümleri altında bulunur.

|Özellik|Açıklama|
|-|-|
|Etki Alanı Özelliği|Xml serileştirme yapılandırma verisi uygulandığı özellik. Salt okunur.|
|Bilinen Anahtar|True ise, özelliği bu etki alanı sınıfının örneklerine başvurulan bilinen adlar oluşturmak için anahtar olarak kullanılır.|
|Bilinen Ad Niteleyicisi|True ise, özelliği bilinen adlarda niteleyici oluşturmak için kullanılır. false ise ve Bu etki alanı sınıfı için SerializeId true ise, bilinen adlar ekleme ağacında üst öğenin bilinen adı tarafından tam olarak kullanılır.|
|Gösterimi|Öznitelik ise, özelliği bir xml özniteliği olarak serileştirilmiştir; if Öğesi, bir öğe olarak seri hale getirilir; Yoksay ise, seri hale getirlanmaz.|
|Xml Adı|Xml özniteliği veya özelliğini temsil eden öğe için kullanılan ad. Varsayılan olarak, bu etki alanı özellik adının küçük harfli bir sürümüdür.|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar|

### <a name="xml-role-data"></a>Xml Rolü verileri

Rol veri düğümleri, kaynak sınıf düğümleri altında bulunur.

|Özellik|Açıklama|
|-|-|
|Özel Bilinen Ad Var|Bu ilişkiden geçen bilinen adlar oluşturmak ve çözümlemek için kendi kodunuzu sağlamak için bunu true olarak ayarlayın.<br /><br /> Ayrıntılı yönergeler için çözümü derleme ve ardından hata iletilerine çift tıklayın.|
|Etki Alanı İlişkisi|Bu seçeneklerin geçerli olduğu ilişkiyi belirtir. Salt okunur.|
|Öğesi Atla|True ise, kaynak role karşılık gelen XML düğümü şemadan atlanır.<br /><br /> Kaynak ve hedef sınıflar arasında birden fazla ilişki varsa, bu rol düğümü iki ilişkiye ait bağlantılar arasında ayrımlar sağlar. Bu nedenle, bu durumda bu seçeneği ayarlamamanizi öneririz.|
|Rol Öğesi Adı|Kaynak rolden türetilen XML öğesinin adını belirtir. Varsayılan değer rol özelliği adıdır.|
|Tam Formu Kullanma|True ise, her hedef öğe veya bilinen ad, ilişkiyi temsil eden bir XML düğümü içine alınır. İlişkinin kendi etki alanı özellikleri varsa bu true olarak ayar olmalıdır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
