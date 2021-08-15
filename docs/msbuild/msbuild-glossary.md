---
title: MSBuild sözlüğü
description: yapı altyapısını ve bileşenlerini tanımlayan Microsoft Build Engine (MSBuild) sözlüğü koşullarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c790281dbe3edc21ce5b9961790a91853a4f2ce30099fdcd02afb98fe9a879d2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121316350"
---
# <a name="msbuild-glossary"></a>MSBuild sözlüğü

bu terimler Microsoft Build Engine (MSBuild) ve bileşenlerini tanımlamakta kullanılır.

## <a name="assemblyfoldersex"></a>AssemblyFoldersEx

Üçüncü taraf satıcıların, tasarım zamanı çözümlemenin başvuru derlemelerini bulmak için nerede görünebileceği, desteklediği her bir sürüm için yolları depolayacağı bir kayıt defteri konumu.

## <a name="batching"></a>toplu işleme

Toplu işleme öğeleri, öğe meta verileri temelinde *toplu* iş olarak bilinen farklı kategorilere bölmek ve sonra her toplu işi kullanarak bir kez hedef veya görev çalıştırmak anlamına gelir. toplu işleme, for--loop yapısının MSBuild eşdeğeridir. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.

## <a name="build-scope"></a>Yapı kapsamı

yapı kapsamı, bir proje için ve çok projeli bir derlemede oluşturulan herhangi bir alt proje için görünebilir olan genel bir özellik gibi MSBuild nesnesini açıklar.

## <a name="child-project"></a>alt proje

Bkz. *Proje, alt*.

## <a name="condition"></a>koşul

birçok MSBuild öğesi koşullu olarak tanımlanabilir; diğer bir deyişle, `Condition` özniteliği öğesinde görüntülenir. Koşul olarak değerlendirilmediği takdirde koşullu öğelerin içeriği yoksayılır `true` . Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).

## <a name="definition-item"></a>Tanım, öğe

*Öğe tanımına* bakın.

## <a name="emit-item"></a>öğeyi yay

Bir yapılandırmanın yürütme aşamasında, öğeleri özniteliği olan alt öğeleri olan görevler tarafından oluşturulabilir veya değiştirilebilir `Output` `ItemName` . Görev, yeni öğeleri "yayma" olarak kabul edilir.

## <a name="emit-property"></a>özelliği yay

Bir yapı yürütme aşamasında özellikler, özniteliği olan alt öğeleri olan görevler tarafından oluşturulabilir veya değiştirilebilir `Output` `PropertyName` . Görev, yeni özelliği "yayma" olarak kabul edilir.

## <a name="evaluation-phase"></a>değerlendirme aşaması

Değerlendirme, proje derlemesinin ilk aşamasıdır. Tüm özellikler ve öğeler, projede göründükleri sırayla değerlendirilir. İçeri aktarılan projeler, projede karşılaştığı şekilde değerlendirilir. Hedefler ve görevler, yürütme aşamasına kadar çalışmaz ve bildirildikleri ya da yayma işlemleri değerlendirme sırasında yok sayılır.

## <a name="execution-phase"></a>yürütme aşaması

Yürütme, proje derlemesinin ikinci aşamasıdır. Seçilen hedefler oluşturulur ve görevler çalıştırılır. Özellikler ve öğeler, değerlendirme değerleriyle karşılaştırıldığında oluşturulabilir veya değiştirilebilir.

## <a name="function-property"></a>Function, Property

Bkz. *Özellik işlevi*.

## <a name="function-item"></a>işlev, öğe

Bkz. öğe işlevi.

## <a name="item"></a>öğe

Öğeler, derleme sistemine giriş ve öğe adlarına göre öğe türlerine göre gruplandırılır. Öğeler genellikle dosyaları temsil eder. Öğeler ait oldukları öğe türüne göre adlandırıldıklarından, hüküm *öğesi* ve *öğe değeri* birbirlerinin yerine kullanılabilir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

## <a name="item-definition"></a>öğe tanımı

Öğe tanımı grupları herhangi bir öğe türüne varsayılan meta veri ekleyen öğe tanımlarını içerir. İyi bilinen meta veriler gibi, varsayılan meta veriler belirtilen öğe türünün tüm öğeleriyle ilişkilendirilir. Varsayılan meta veriler, bir öğe tanımında açıkça geçersiz kılınabilir. Daha fazla bilgi için bkz. [öğe tanımları](../msbuild/item-definitions.md).

## <a name="item-function"></a>item işlevi

Öğe işlevleri, projedeki öğeler hakkında bilgi alır. Bu işlevler ayrı () öğeleri almayı basitleştirir ve öğeler aracılığıyla döngüden daha hızlıdır. Öğe yollarını ve dizeleri işlemek için işlevler vardır. Daha fazla bilgi için bkz. [öğe işlevleri](../msbuild/item-functions.md).

## <a name="item-metadata"></a>öğe meta verileri

Bkz. *meta veriler, öğe*.

## <a name="item-type"></a>öğe türü

Öğe türleri, görevler için parametre olarak kullanılabilecek öğelerin adlandırılmış listeleridir. Görevler, yapı işleminin adımlarını gerçekleştirmek için öğe değerlerini kullanır. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

## <a name="metadata-item"></a>meta veri, öğe

Öğe meta verileri bir öğeyle ilişkili ad-değer çiftleri koleksiyonudur. Meta veriler, öğe için açıklayıcı bilgiler sağlar ve iyi bilinen meta veriler dışında isteğe bağlıdır. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

## <a name="metadata-well-known"></a>meta veriler, iyi bilinen

İyi bilinen meta veriler önceden tanımlanmış bir değer kullanılarak başlatılan salt okunurdur. İyi bilinen meta veriler, bir dosyaya başvuran bir öğe için açıklayıcı bilgiler sağlar. Örneğin, adlı iyi bilinen meta verilerin değeri, `FullPath` başvurulan dosyanın tam yoludur. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

## <a name="multitargeting"></a>çoklu sürüm desteği

bir uygulama veya derleme projesinin birçok farklı CLR ve çerçevesini MSBuild ve Visual Studio bir şekilde hedefleyebilme özelliği.

## <a name="profile"></a>profil

Tam Framework 'ün bir alt kümesi. Bu, bir makineye indirilmesi gereken miktarı en aza indirmek için kullanılır.

## <a name="project-file"></a>Proje dosyası

proje dosyası, derlemeyi denetleyen MSBuild betiğini içerir. Project dosyalar genellikle *. csproj* veya *. vbproj* gibi *proj* ile biten bir dosya uzantısına sahiptir. Project dosya, özellik dosyalarını ve hedef dosyaları içeri aktarabilir.

## <a name="property"></a>özellik

Özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="property-environment"></a>Özellik, ortam

Ortam özelliği, aynı ada sahip bir sistem ortam değişkeninin değerine otomatik olarak başlatılan bir özelliktir. daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="property-file"></a>Özellik dosyası

Özellik dosyası, derleme kılavuzunu oluşturan genellikle özellik gruplarını ve öğe gruplarını içeren bir proje dosyasıdır. Kurala göre, *. props* dosya uzantısına sahiptir. Özellik dosyaları genellikle ilişkili proje dosyalarının başlangıcında içeri aktarılır.

## <a name="property-function"></a>Property, Function

özellik işlevi, MSBuild betikleri değerlendirmek için kullanılabilen bir sistem özelliğidir veya yöntemidir. Özellik yöntemleri, sistem saatini okumak, dizeleri karşılaştırmak, normal ifadelerle eşleştirmek ve diğer işlemleri gerçekleştirmek için kullanılabilir. Daha fazla bilgi için bkz. [özellik işlevleri](../msbuild/property-functions.md).

## <a name="property-function-nested"></a>Özellik işlevi, iç içe

Özellik işlevleri, daha karmaşık işlevler oluşturmak için birleştirilebilir. Örneğin,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Daha fazla bilgi için bkz. [özellik işlevleri](../msbuild/property-functions.md).

## <a name="property-global"></a>Özellik, genel

Genel özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. genel özellikler bir komut isteminde veya `Properties` bir [MSBuild görevinin](../msbuild/msbuild-task.md)özniteliği kullanılarak ayarlanır ve bir yapılandırmanın değerlendirme aşamasında değiştirilemez. daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="property-local"></a>özellik, yerel

Yerel özellik, derleme işlemini kontrol etmek için kullanılan bir anahtar-değer çiftidir. Bu terim yalnızca genel özellik olan bir özelliği ayırt etmek için kullanılır.

## <a name="property-registry"></a>özellik, kayıt defteri

Kayıt defteri özelliği, bir sistem kayıt defteri alt anahtarının değerini okumak için özel bir söz dizimi kullanılarak ayarlanmış bir değere sahiptir. Daha fazla bilgi için [bkz. MSBuild.](../msbuild/msbuild-properties.md).

## <a name="property-reserved"></a>özellik, ayrılmış

Ayrılmış özellik, derleme işlemini kontrol etmek için kullanılan bir anahtar-değer çiftidir. Ayrılmış özellikler önceden tanımlanmış değerlere otomatik olarak başlatılır. Daha fazla bilgi için [bkz. MSBuild.](../msbuild/msbuild-properties.md).

## <a name="project-scope"></a>proje kapsamı

Project kapsamı, MSBuild içeren proje dosyasında ve içeri aktaran tüm projelerde görünür olan bir yerel özellik gibi bir nesne tanımlar.

## <a name="project-child"></a>project, child

Alt proje, proje derlemesi MSBuild görev tarafından oluşturulur. Bu yeni proje, görevle ilgili görevi içeren hedefi içeren veya içeri aktaran projenin MSBuild olur. Alt proje, özniteliği tarafından değiştirilmediği sürece üst projenin genel özelliklerini `Properties` devralır.

## <a name="redist-list"></a>redist list

Yeniden dağıtım listesi: Verilen çerçeveye karşılık gelen derlemelerin listesi.

## <a name="reference-assembly"></a>başvuru derlemesi

Bir uygulama oluşturmak için tasarım zamanında kullanılan bir derleme. Bir başvuru derlemesi, yalnızca meta verileri ve genel arabirimleri bırakarak gerçek kodu ve özel arabirimleri kaldırabilir.

## <a name="registry-property"></a>registry özelliği

Bkz. *özelliği, kayıt defteri.*

## <a name="target"></a>Hedef

Hedef, görevleri belirli bir sırada gruplar ve proje dosyasının bölümlerini derleme sürecine giriş noktaları olarak gösterir. Daha fazla bilgi için [bkz. Hedefler.](../msbuild/msbuild-targets.md)

## <a name="target-building"></a>hedef, bina

Bkz. hedef, çalışıyor.

## <a name="target-evaluating"></a>hedef, değerlendirme

Artımlı derleme nedeniyle, özelliklerde ve öğelerde olası değişiklikler için hedeflerin analizlenmesi gerekir. Hedef atlanmış olsa bile bu değişikliklerin yapılmış olması gerekir. Hedefin değerlendirilmesi, bu analizi gerçekleştirmek ve bu değişiklikleri yapmak anlamına gelir. Daha fazla bilgi için bkz. [Artımlı derlemeler.](../msbuild/incremental-builds.md)

## <a name="target-executing"></a>hedef, yürütme

Bir hedefin yürütülmesi, onu değerlendirmek ve koşulları olmayan veya koşulları doğru olarak değerlendirilen tüm görevleri yürütmek anlamına gelir. Artımlı derleme sırasında hedefler atlanabilir veya yürütülür, ancak her zaman değerlendirilir. Daha fazla bilgi için bkz. hedef, değerlendirme.

## <a name="target-running"></a>target, running

False olarak değerlendirilen bir koşula sahip hedef çalıştırlanmaz, yani derleme üzerinde hiçbir etkisi yoktur. Çalıştıran hedefler yürütülür veya atlanır. Her iki durumda da hedef değerlendirilir. Daha fazla bilgi için bkz. hedef, değerlendirme.

## <a name="target-skipping"></a>hedef, atlama

Artımlı derleme tüm çıkış dosyalarının güncel olduğunu belirlerse hedef atlanır, yani hedef değerlendirilir, ancak hedef içindeki görevler yürütülmez. Daha fazla bilgi için bkz. hedef, değerlendirme.

## <a name="target-framework-moniker"></a>hedef çerçeve bilinen adı

Çerçeveyi açıklayan bir ad (örneğin, . NETFramework, Silverlight, vb.), sürümü ve hedeflemek istediğiniz profil (İstemci, Sunucu vb.).

## <a name="targeting-pack"></a>targeting pack

Verilen bir çerçeve ile dağıtılan derlemelerin listesi ve bu çerçeve için başvuru derlemeleri kümesi.

## <a name="targets-file"></a>targets dosyası

Hedefler dosyası, çoğunlukla derlemeye kılavuz olan hedefleri ve görevleri içeren bir proje dosyasıdır. Kural gereği, *.targets dosya uzantısına sahip* olur. Hedef dosyalar genellikle ilişkili proje dosyalarının sonunda içe aktarılır.

## <a name="task"></a>görev

Görevler, projelerin derleme işlemlerini gerçekleştirmek için MSBuild yürütülebilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derler veya bir dış araç çalıştırabilirsiniz. Daha fazla bilgi için bkz. [Görevler.](../msbuild/msbuild-tasks.md)

## <a name="transform"></a>transform

Dönüştürme, bir öğe koleksiyonunun diğerine dönüştürülmesidir. Bir projenin öğe koleksiyonlarını dönüştürmesini etkinleştirmeye ek olarak, dönüştürme bir hedefin girişleri ve çıkışları arasında doğrudan eşlemeyi tanımlamasını sağlar. Daha fazla bilgi için bkz. [Dönüşümler.](../msbuild/msbuild-transforms.md)

## <a name="well-known-metadata"></a>iyi bilinen meta veriler

Bilinen *meta verilere bakın.*

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
