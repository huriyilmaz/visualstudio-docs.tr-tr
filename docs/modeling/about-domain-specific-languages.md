---
title: Etki Alanına Özgü Diller Hakkında
description: Etki alanına özgü bir dilin (DSL) belirli bir sorun alanında veya etki alanında deyimleri ifade etmek için nasıl tasarlan olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab56292aafda25efc0b3dfeeb14e93d4502a5567
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384986"
---
# <a name="about-domain-specific-languages"></a>Etki Alanına Özgü Diller Hakkında

C# veya UML gibi genel amaçlı bir dilden farklı olarak, etki alanına özgü bir dil (DSL), belirli bir sorun alanında veya etki alanında deyimleri ifade etmek için tasarlanmıştır.

Bilinen DSL'ler normal ifadeleri ve SQL'i içerir. Her DSL, metin dizeleri veya veritabanı işlemleri için genel amaçlı bir dilden çok daha iyidir, ancak kendi kapsamı dışındaki fikirleri açıklama konusunda çok daha kötüdür. Tek tek sektörlerin de kendi DSL'leri vardır. Örneğin, telekomünikasyon sektöründe çağrı açıklaması dilleri bir telefon çağrısında eyalet dizisini belirtmek için yaygın olarak kullanılır ve hava seyahati sektöründe uçuş rezervasyonlarını tanımlamak için standart bir DSL kullanılır.

İşletmeniz ve projeniz, DSL ile tanımlanebilecek özel kavram kümeleriyle de ilgilenmektedir. Örneğin, bu uygulamalardan biri için DSL tanımlayabilirsiniz:

- Web sitesinde gezinti yollarını planlama.

- Elektronik bileşenler için kablolama diyagramları.

- Havaalanı için taşıyıcı bantlar ve taşıma ekipmanları ağları.

DSL tasarladığınız zaman etki  alanındaki web sayfası, lamp veya havaalanı iade masası gibi önemli kavramların her biri için bir etki alanı sınıfı tanımlarsiniz. Kavramları bir *araya bağlayarak* köprü, kablo veya taşıyıcı bant gibi etki alanı ilişkilerini tanımlarız.

DSL'nizin kullanıcıları model *oluşturabilir.* Modeller DSL *örnekleridir.* Örneğin, belirli bir web sitesini veya belirli bir cihazın kablolarını ya da belirli bir havaalanının içinde yer alan yolcu işleme sistemini açıklar.

Kullanıcılarınız bir modeli diyagram veya Windows formu olarak görüntülemenizi sağlar. Modeller xml olarak da görünüme sahip olabilir ve bu şekilde depolanır. DSL tanımladığınız zaman, her bir etki alanı sınıfının ve ilişkinin örneklerinin kullanıcı ekranında nasıl görüneceğini tanımlarsiniz. Tipik bir DSL, oklarla bağlanmış simgeler veya dikdörtgenler koleksiyonu olarak görüntülenir.

Aşağıdaki şekilde, diyagram dsl'sinde küçük bir model gösterildi:

![Tudor Aile Ağacı Modeli](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>DSL'lerle neler yapabiliriz?

DSL'nin tipik bir uygulaması, program kodu veya diğer yapıtlar oluşturmaktır. DSL'nizi tanımlarken, DSL *modelinin okunan* ve metin dosyaları oluşturan metin şablonları tanımlayabilirsiniz.

Örneğin, bir havaalanı planı alan ve kabul işleme yazılımının bir kısmını oluşturan şablonların yanı sıra planı açıklayan bazı kullanıcı belgelerini de yazabilirsiniz.

BIR DSL tanımlandığı zaman, bunu kendi bilgisayarlarına yük bindiren diğer kullanıcılara dağıtabilirsiniz. DSL'nizin kullanıcıları, model oluşturma ve düzenleme Visual Studio.

Ayrıca, kullanıcıların DSL'yi düzenlemesine yardımcı olan menü komutlarını ve diğer araçları, DSL'nin doğru şekilde kullanıldıklarından emin olmak için doğrulama kısıtlamaları ve kullanıcıların yeni örnekler oluşturmasına yardımcı olan öğe şablonları tanımlayabilirsiniz. Bir veya daha fazla DSL'i araçlarıyla ve diğer Visual Studio tümleşik paket olarak sarmaabilirsiniz.

Genellikle, bir geliştirme ekibinin birkaç ürün için benzer kod yazması gereken etki alanına özgü bir dil oluşturulur. Örneğin, işleme sistemlerinde uzman olan bir şirket, her yükleme için bazı kodlar oluştura bir DSL izlemesi tanımlayabilir. DSL'nin avantajları, müşterileri tarafından anlaşılabilir, bu koddan oluşturulan kodun güvenilir olması ve müşterilerin gereksinimleri değişirse sistemin hızlı bir şekilde güncelleştirilebilir olmasıdır.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] kendi grafik tasarımcınızı ve kendi diyagram gösteriminizi olan etki alanına özgü bir dil oluşturmanızı ve ardından dili kullanarak her proje için uygun kaynak kodunu oluşturmanızı sağlar.

## <a name="domain-specific-development"></a>Domain-Specific Geliştirme

Etki alanına özgü geliştirme, uygulamalarınızı etki alanına özgü bir dil kullanılarak modellandıran parçaları tanımlama ve ardından dili oluşturma ve uygulama geliştiricilerine dağıtma işlemidir. Geliştiriciler, uygulamalarına özgü modeller oluşturmak, modelleri kullanarak kaynak kodu oluşturmak ve ardından uygulamaları geliştirmek için kaynak kodu kullanmak için etki alanına özgü dili kullanır.

## <a name="aspects-of-graphical-domain-specific-development"></a>Grafik ve Geliştirme Domain-Specific Yönleri

Grafik etki alanına özgü bir dil aşağıdaki özellikleri içermeli:

- Gösterim

- Etki alanı modeli

- Yapıt oluşturma

- Serileştirme

- Visual Studio ile Tümleştirme

### <a name="notation"></a>Gösterim

Etki alanına özgü bir dil, etki alanına özgü yapıları temsil edecek şekilde kolayca tanımlanabiliyor ve genişletilen makul düzeyde küçük bir öğe kümesine sahip olmalıdır. Gösterimi, öğeleri temsil eden şekiller ve grafik diyagram yüzeyinde öğeler arasındaki ilişkileri temsil eden bağlayıcılardan oluşur. 'de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] şekiller, etki alanına özgü dilinizin öğelerini temsil edecek şekilde genişletilmiş ve iyileştirilmiş olabilir.

### <a name="domain-model"></a>Etki Alanı Modeli

Etki alanına özgü bir dil, öğe kümesiyle aralarındaki ilişkileri tutarlı bir dil bilgisi olarak birleştirmeli. Ayrıca öğe ve ilişki birleşimlerinin geçerli olup olmadığını da tanımlaması gerekir. Örneğin, programlama dilleri genellikle döngüsel devralmayı önler; burada bir sınıf ikinci sınıftan türetilen ve ikinci sınıf birinci sınıftan türetilen. Kısıtlamalar iş mantığını ifade etmek için de kullanılabilir; örneğin, bir kişi kendisine bağımlı olamaz. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , çoğu etki alanına özgü dilin ihtiyaç duyduğu kısıtlama çeşitlerini ifade etmek için kısıtlamaları kullanır.

### <a name="artifact-generation"></a>Yapıt Oluşturma

Etki alanına özgü dilin ana amaçlarından biri, kaynak kod, XML dosyası veya başka bir kullanılabilir veri gibi bir yapıt oluşturmaktır. Modelde yapılan bir değişiklik genellikle yapıtta bir değişiklik anlamına gelir. kullanarak [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] yapıtları üretin ve modeli değiştirirken bunları yeniden üretin.

### <a name="serialization"></a>Serileştirme

Etki alanına özgü bir dil düzenlenemez, kaydedilebilir, kapatılacak ve yeniden yüklenecektir. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , etki alanına özgü dilinizin seri hale getirme veya kalıcı hale getirme biçimini tanımlamanızı ve özelleştirmenizi sağlayan bir XML biçimi kullanır.

### <a name="integration-with-visual-studio"></a>Visual Studio ile Tümleştirme

bir [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] konakta barındır Visual Studio, birçok farklı pencereyi ve Visual Studio genişleter. Ayrıca menü komutlarının, araç kutusu öğelerinin ve kullanıcı arabiriminin diğer öğelerinin davranışını özelleştirmenize de olanak sağlar.

Etki alanına özgü diliniz için model veri verisi bağdaştırıcısı da oluşturabilirsiniz. Bu bağdaştırıcı bir modele ve model içindeki öğelere başvurup DSL örneğine erişen ve güncelleştiren kod yazmanıza olanak sağlar. Güçlü Model Veri Veri Visual Studio kullanarak birden çok modelle Visual Studio uzantılar yazabilirsiniz. Ayrıca, modellerle birlikte çalışmak için tek başına uygulamalar da yazabilirsiniz. Daha fazla bilgi için [bkz. Visual Studio Modelbus kullanarak Modelleri Tümleştirme.](../modeling/integrating-models-by-using-visual-studio-modelbus.md)

## <a name="benefits-of-domain-specific-development"></a>Domain-Specific Geliştirmenin Avantajları

Etki alanına özgü bir dil aşağıdaki avantajları sağlar:

- Sorun alanıyla tam olarak uygun yapıları içerir.

     Genel amaçlı dillerden farklı olarak, etki alanına özgü bir dil, sorun alanının mantığını doğrudan temsil eden öğelerden ve ilişkilerden oluşur. Örneğin, bir sigorta ilkesi uygulaması ilkeler ve talepler için öğeler içermeli. Etki alanına özgü bir dil, uygulamayı tasarlamayı ve mantık hatalarını bulup düzeltmeyi kolaylaştırır.

- Geliştirici olmayanların ve etki alanını bilmiyor olan kişilerin genel tasarımı anlarını sağlar.

     Grafik etki alanına özgü bir dil kullanarak, geliştirici olmayanların uygulamanın tasarımını kolayca anlayabilirsiniz.

- Son uygulamanın prototipini oluşturmanızı kolaylaştırır.

     Geliştiriciler, modellerinin oluşturdukları kodu kullanarak istemcilere göstere bir prototip uygulama oluşturabilir.

## <a name="the-process-of-domain-specific-development"></a>Domain-Specific Geliştirme Süreci

Etki alanına özgü diller kullanan çoğu yazılım geliştirme ekibi, modellerini oluşturmak ve kullanmak için şu adımları izleyin:

- Ekip, etki alanının değişken bölümlerini hiçbir zaman değişmeden ayırt ediyor.

- Geliştiriciler sabit parçalar için kod yazar ve değişken parçaları için uzantı noktalarını bırakır.

- Baş yazılım geliştiricisi veya mimar, etki alanının sabit bölümlerinin tasarım desenlerini ve değişken parçaların uzantı noktalarını içeren etki alanına özgü bir dil oluşturur.

- Baş yazılım geliştiricisi veya mimar, ekibin ürettiği çeşitli uygulamaların geliştiricilerine etki alanına özgü dili dağıtır.

- Her geliştirici, belirli bir uygulama için geçerli olan bir model oluşturur.
