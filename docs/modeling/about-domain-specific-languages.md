---
title: Etki Alanına Özgü Diller Hakkında
description: Belirli bir sorun alanındaki veya etki alanındaki deyimleri ifade etmek için bir etki alanına özgü dilin (DSL) nasıl tasarlandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 54eeb75a623a7c20d0fad3f5f66e30c0b4617558
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069424"
---
# <a name="about-domain-specific-languages"></a>Etki Alanına Özgü Diller Hakkında

C# veya UML gibi genel amaçlı bir dilin aksine, etki alanına özgü dil (DSL) belirli bir sorun alanı veya etki alanındaki deyimleri ifade etmek için tasarlanmıştır.

İyi bilinen DSLs 'ler, normal ifadeleri ve SQL içerir. Her DSL, metin dizelerindeki veya bir veritabanında işlemleri açıklamak için genel amaçlı dilden çok daha iyidir, ancak kendi kapsamı dışında kalan fikirleri açıklamak için çok daha kötülük olur. Her sektörde kendi DSLs 'Leri de vardır. Örneğin, telekomünikasyon sektöründe çağrı açıklaması dilleri bir telefon çağrısındaki durumların sırasını belirtmek için yaygın olarak kullanılır ve hava yolculuğu sektöründe uçuş rezervasyonlarını anlatmak için standart DSL kullanılır.

İşletmeniz ve projeniz, bir DSL ile açıklanacak özel kavram kümeleriyle de ilgilenir. Örneğin, bu uygulamalardan biri için DSL tanımlayabilirsiniz:

- Bir Web sitesindeki gezinti yollarının planı.

- Elektronik bileşenler için bağlantı şemaları.

- Bir Havaalanı için taşıyıcı ve bagaj işleme donatısı ağları.

Bir DSL tasarladığınızda, etki alanındaki bir Web sayfası, lamba veya Havaalanı iade masası gibi önemli kavramların her biri için bir *etki alanı sınıfı* tanımlarsınız. Kavramları birbirine bağlamak için köprü, tel veya bir taşıyıcı bant gibi *etki alanı ilişkileri* tanımlarsınız.

DSL oluşturma *modellerinizin kullanıcıları.* Modeller DSL *örnekleridir* . Örneğin, belirli bir Web sitesini veya belirli bir cihazın kablolarını veya belirli bir Havaalanı içindeki Bagaj işleme sistemini tanımlarlar.

kullanıcılarınız bir modeli diyagram olarak veya Windows formu olarak görüntüleyebilir. Modeller, depolandıkları bir XML olarak da görüntülenebilir. Bir DSL tanımladığınızda, her bir etki alanı sınıfının ve ilişkinin örneklerinin Kullanıcı ekranında nasıl göründüğünü tanımlarsınız. Tipik bir DSL, oklar ile bağlı bir simgeler veya dikdörtgenler koleksiyonu olarak görüntülenir.

Aşağıdaki şekilde, bir diagrammatik DSL 'de küçük bir model gösterilmektedir:

![Tuçi aile ağacı modeli](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>DSLs ile yapabilecekleriniz

Bir DSL 'nin tipik bir uygulaması, program kodu veya diğer yapıtlar oluşturmak için kullanılır. DSL 'yi tanımlarken, DSL modelini okuyan ve metin dosyaları oluşturabileceğiniz *metin şablonları* tanımlayabilirsiniz.

Örneğin, bir Havaalanı planı alan ve bagaj işleme için yazılımın bir parçasını oluşturan şablonlar yazabilir ve planı tanımlayan bazı Kullanıcı belgeleri de oluşturabilirsiniz.

Bir DSL tanımladığınızda, onu kendi bilgisayarlarına yükleyebilen diğer kullanıcılara dağıtabilirsiniz. DSL kullanıcıları Visual Studio modeller oluşturup düzenleyebilir.

Ayrıca, kullanıcıların DSL 'yi doğru şekilde kullanmasının yanı sıra kullanıcıların yeni örnekler oluşturmalarına yardımcı olan öğe şablonları ve DSL, doğrulama kısıtlamalarını düzenleyebilmesi için yardım eden menü komutlarını ve diğer araçları da tanımlayabilirsiniz. bir veya daha fazla dsls 'yi, araçları ve diğer Visual Studio uzantılarına tümleşik bir paket olarak sardırabilirsiniz.

Genellikle, bir geliştirme ekibinin çeşitli ürünler için benzer kod yazması gerektiğinde, etki alanına özgü bir dil oluşturulur. Örneğin, Bagaj işleme sistemlerinde uzmanlaşmış bir şirket, her yükleme için kodun bir kısmını oluşturabileceği bir Bagaj iz DSL tanımlayabilir. DSL 'nin avantajları, müşterileri tarafından anlaşılabilmesini, bundan üretilen kodun güvenilir olmasını ve müşterilerin gereksinimlerinin değiştirilmesi durumunda sistemin hızla güncelleştirilemeyebilir.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] kendi grafik tasarlamanızı ve kendi diyagram gösteriminizi içeren, etki alanına özgü bir dil oluşturmanızı sağlar ve ardından bu dili kullanarak her proje için uygun kaynak kodu oluşturabilirsiniz.

## <a name="domain-specific-development"></a>Domain-Specific geliştirme

Etki alanına özgü geliştirme, etki alanına özgü bir dili kullanarak modellenebilir uygulamalarınızın parçalarını belirleme ve sonra dili oluşturup uygulama geliştiricilerine dağıtma işlemidir. Geliştiriciler, uygulamalarına özel modeller oluşturmak için etki alanına özgü dili kullanır, kaynak kodu oluşturmak için modelleri kullanır ve ardından uygulama geliştirmek için kaynak kodunu kullanır.

## <a name="aspects-of-graphical-domain-specific-development"></a>Grafik Domain-Specific geliştirmenin yönleri

Grafik etki alanına özgü dil aşağıdaki özellikleri içermelidir:

- Gösterim

- Etki alanı modeli

- Yapıt oluşturma

- Serileştirme

- Visual Studio ile Tümleştirme

### <a name="notation"></a>Gösterim

Alana özgü bir dilin, etki alanına özgü yapıları temsil etmek üzere kolayca tanımlanabilen ve genişletilebilen, makul bir öğe kümesine sahip olması gerekir. Bir gösterim, bir grafik diyagram yüzeyinde öğeler arasındaki ilişkileri temsil eden öğeleri ve bağlayıcıları temsil eden şekillerden oluşur. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]' De, şekiller, etki alanına özgü dilin öğelerini göstermek için genişletilebilir ve iyileştirilmiş olabilir.

### <a name="domain-model"></a>Etki alanı modeli

Etki alanına özgü bir dilin öğe kümesini ve bunlarla arasındaki ilişkileri tutarlı bir dilbilgisinde birleştirmelidir. Ayrıca, öğe ve ilişkilerin birleşimlerinin geçerli olup olmadığını da tanımlamalıdır. Örneğin, programlama dilleri genellikle, bir sınıfın ikinci bir sınıftan türetildiği ve ikinci sınıf birinci sınıftan türetildiği dairesel devralmayı önler. Kısıtlamalar, iş mantığını ifade etmek için de kullanılabilir. Örneğin, bir kişi hımself öğesinin bağımlı olamaz. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , etki alanına özgü dillerin çoğunun gerektirdiği kısıtlama türlerini ifade etmek için kısıtlamaları kullanır.

### <a name="artifact-generation"></a>Yapıt oluşturma

Etki alanına özgü dilin ana amaçlarından biri, örneğin, kaynak kodu, XML dosyası veya başka bir kullanılabilir veri gibi bir yapıt oluşturmak içindir. Genellikle modeldeki bir değişiklik yapıtın bir değişikliği anlamına gelir. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]Yapıtları oluşturmak ve modeli değiştirirken yeniden oluşturmak için ' i kullanabilirsiniz.

### <a name="serialization"></a>Serileştirme

Düzenlenebilen, kaydedilebilen, kapatılan ve yeniden yüklenmiş bir biçimde, etki alanına özgü bir dilin kalıcı olması gerekir. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , etki alanına özgü dilin serileştirilme veya kalıcı hale getirilme şeklini tanımlamanıza ve özelleştirmenize imkan tanıyan bir XML biçimi kullanır.

### <a name="integration-with-visual-studio"></a>Visual Studio ile Tümleştirme

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]Visual Studio içinde barındırıldığından, birçok Visual Studio pencereleri ve denetimi genişletir. Ayrıca, menü komutlarının, araç kutusu öğelerinin ve Kullanıcı arabiriminin diğer öğelerinin davranışını özelleştirmenizi sağlar.

Ayrıca, etki alanına özgü diliniz için bir model veri yolu bağdaştırıcısı da oluşturabilirsiniz. Bu bağdaştırıcı, bir model içindeki model ve öğelere başvurmanıza ve DSL örneğine erişebilen ve güncelleştiren bir kod yazmanıza olanak tanır. güçlü Model veri yolu mekanizmasını kullanarak, birden çok modelle çalışan Visual Studio uzantıları yazabilirsiniz. Ayrıca, modellerle çalışan tek başına uygulamalar yazabilirsiniz. daha fazla bilgi için bkz. [Visual Studio Modelbus kullanarak modelleri tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Domain-Specific geliştirmenin avantajları

Etki alanına özgü bir dil aşağıdaki avantajları sağlayabilir:

- Sorun alanına tam olarak uyan yapıları içerir.

     Genel amaçlı dillerden farklı olarak, etki alanına özgü bir dil, sorun alanının mantığını doğrudan temsil eden öğe ve ilişkilerden oluşur. Örneğin, bir sigorta ilkesi uygulaması, ilkeler ve talepler için öğeleri içermelidir. Etki alanına özgü bir dil, uygulamayı tasarlamayı ve mantığın hatalarını bulmayı ve düzeltmeyi kolaylaştırır.

- Geliştiricilerin ve etki alanını kullanmayan kişilerin genel tasarımı anlayabilmesini sağlar.

     Grafik etki alanına özgü bir dil kullanarak, geliştiricilerin uygulamanın tasarımını kolayca anlayabilmesi için etki alanının görsel bir gösterimini oluşturabilirsiniz.

- Son uygulamanın prototip oluşturmayı kolaylaştırır.

     Geliştiriciler, istemcilerinin istemcilere gösterebilecekleri bir prototip uygulaması oluşturmak için kendi modelinin oluşturduğu kodu kullanabilir.

## <a name="the-process-of-domain-specific-development"></a>Domain-Specific geliştirme Işlemi

Etki alanına özgü diller kullanan çoğu yazılım geliştirme ekibi, modellerini oluşturmak ve kullanmak için aşağıdaki adımları izler:

- Takım, etki alanının değişken kısımlarını hiçbir şekilde değişmeme bölümlerinden ayırır.

- Geliştiriciler sabit parçalar için kod yazar ve değişken parçaları için uzantı noktaları bırakır.

- Lider yazılım geliştiricisi veya mimarı, etki alanının sabit bölümlerinin tasarım düzenlerini ve değişken bölümlerinin uzantı noktalarını içeren, etki alanına özgü bir dil oluşturur.

- Lider yazılım geliştiricisi veya mimarı, etki alanına özgü dili ekibin ürettiği çeşitli uygulamaların geliştiricilerine dağıtır.

- Her geliştirici, belirli bir uygulama için geçerli olan bir model oluşturur.
