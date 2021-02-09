---
title: MSBuild sözlüğü
description: Yapı altyapısını ve bileşenlerini tanımlayan Microsoft Build Engine (MSBuild) sözlüğü koşullarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6e5ef85ffc4a10719cfbef79cbaf6dad08bdbf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919121"
---
# <a name="msbuild-glossary"></a>MSBuild sözlüğü

Bu terimler Microsoft Build Engine (MSBuild) ve bileşenlerini tanımlamakta kullanılır.

## <a name="assemblyfoldersex"></a>AssemblyFoldersEx

Üçüncü taraf satıcıların, tasarım zamanı çözümlemenin başvuru derlemelerini bulmak için nerede görünebileceği, desteklediği her bir sürüm için yolları depolayacağı bir kayıt defteri konumu.

## <a name="batching"></a>toplu işleme

Toplu işleme öğeleri, öğe meta verileri temelinde *toplu* iş olarak bilinen farklı kategorilere bölmek ve sonra her toplu işi kullanarak bir kez hedef veya görev çalıştırmak anlamına gelir. Toplu işleme, for--Loop yapısının MSBuild eşdeğeridir. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.

## <a name="build-scope"></a>Yapı kapsamı

Yapı kapsamı, bir proje için ve çok projeli bir derlemede oluşturulan herhangi bir alt proje için görünebilir olan genel bir özellik gibi bir MSBuild nesnesini tanımlar.

## <a name="child-project"></a>alt proje

Bkz. *Proje, alt*.

## <a name="condition"></a>koşul

Birçok MSBuild öğesi koşullu olarak tanımlanabilir; diğer bir deyişle, `Condition` özniteliği öğesinde görüntülenir. Koşul olarak değerlendirilmediği takdirde koşullu öğelerin içeriği yoksayılır `true` . Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).

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

Bir uygulama veya derleme projesinin, MSBuild 'den ve Visual Studio 'dan birçok farklı CLR 'nin ve çerçevesini hedefleyebilme özelliği.

## <a name="profile"></a>profil

Tam Framework 'ün bir alt kümesi. Bu, bir makineye indirilmesi gereken miktarı en aza indirmek için kullanılır.

## <a name="project-file"></a>Proje dosyası

Proje dosyası, derlemeyi denetleyen MSBuild betiğini içerir. Proje dosyaları genellikle *. csproj* veya *. vbproj* gibi *proj* ile biten bir dosya uzantısına sahiptir. Proje dosyaları, özellik dosyalarını ve hedef dosyaları içeri aktarabilir.

## <a name="property"></a>özellik

Özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="property-environment"></a>Özellik, ortam

Ortam özelliği, aynı ada sahip bir sistem ortam değişkeninin değerine otomatik olarak başlatılan bir özelliktir. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="property-file"></a>Özellik dosyası

Özellik dosyası, derleme kılavuzunu oluşturan genellikle özellik gruplarını ve öğe gruplarını içeren bir proje dosyasıdır. Kurala göre, *. props* dosya uzantısına sahiptir. Özellik dosyaları genellikle ilişkili proje dosyalarının başlangıcında içeri aktarılır.

## <a name="property-function"></a>Property, Function

Özellik işlevi, MSBuild betiklerini değerlendirmek için kullanılabilen bir sistem özelliğidir veya yöntemidir. Özellik yöntemleri, sistem saatini okumak, dizeleri karşılaştırmak, normal ifadelerle eşleştirmek ve diğer işlemleri gerçekleştirmek için kullanılabilir. Daha fazla bilgi için bkz. [özellik işlevleri](../msbuild/property-functions.md).

## <a name="property-function-nested"></a>Özellik işlevi, iç içe

Özellik işlevleri, daha karmaşık işlevler oluşturmak için birleştirilebilir. Örneğin,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Daha fazla bilgi için bkz. [özellik işlevleri](../msbuild/property-functions.md).

## <a name="property-global"></a>Özellik, genel

Genel özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Genel Özellikler bir komut isteminde veya bir `Properties` [MSBuild görevinin](../msbuild/msbuild-task.md)özniteliği kullanılarak ayarlanır ve bir yapılandırmanın değerlendirme aşamasında değiştirilemez. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="property-local"></a>Özellik, yerel

Yerel bir özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Bu terim yalnızca genel özellik olmayan bir özelliği ayırt etmek için kullanılır.

## <a name="property-registry"></a>Özellik, kayıt defteri

Bir kayıt defteri özelliğinin bir sistem kayıt defteri alt anahtarının değerini okuyan özel bir sözdizimi kullanılarak ayarlanan bir değeri vardır. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="property-reserved"></a>Özellik, ayrılmış

Ayrılmış bir özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Ayrılmış Özellikler otomatik olarak önceden tanımlanmış değerler olarak başlatılır. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="project-scope"></a>Proje kapsamı

Proje kapsamı, örneğin, yalnızca içeren proje dosyasında ve içeri aktardığı herhangi bir projede görünür olan yerel bir özellik gibi bir MSBuild nesnesini tanımlar.

## <a name="project-child"></a>Proje, alt öğe

Bir alt proje, proje derlemesi sırasında MSBuild görevi tarafından oluşturulur. Bu yeni proje, MSBuild görevini içeren hedefi içeren veya içeri aktaran projenin bir alt öğesidir. Alt proje, öznitelik tarafından değiştirilmedikleri takdirde üst projenin genel özelliklerini devralır `Properties` .

## <a name="redist-list"></a>Redist listesi

Yeniden dağıtım listesi: belirli bir çerçeveye karşılık gelen derlemelerin listesi.

## <a name="reference-assembly"></a>başvuru derlemesi

Tasarım zamanı sırasında bir uygulama oluşturmak için kullanılan bir derleme. Bir başvuru derlemesi, gerçek kod ve özel arabirimlerin kaldırılmasına ve yalnızca meta verileri ve genel arabirimleri terk edebilir.

## <a name="registry-property"></a>kayıt defteri özelliği

Bkz. *özellik, kayıt defteri*.

## <a name="target"></a>hedef

Hedef, görevleri belirli bir sırada gruplandırır ve proje dosyasının bölümlerini yapı işlemine giriş noktası olarak gösterir. Daha fazla bilgi için bkz. [hedefler](../msbuild/msbuild-targets.md).

## <a name="target-building"></a>hedef, derleme

Bkz. hedef, çalışıyor.

## <a name="target-evaluating"></a>hedef, değerlendirme

Artımlı derleme nedeniyle, hedefler Özellikler ve öğelerde olası değişiklikler için çözümlenmelidir. Hedef atlansa bile, bu değişikliklerin yapılması gerekir. Bir hedefin değerlendirilmesi, bu çözümlemenin gerçekleştirilmesi ve bu değişikliklerin yapılması anlamına gelir. Daha fazla bilgi için bkz. [Artımlı derlemeler](../msbuild/incremental-builds.md).

## <a name="target-executing"></a>hedef, yürütülüyor

Bir hedefin yürütülmesi, bir koşulu değerlendirmek ve koşulsız tüm görevleri yürütmek ya da koşullarını doğru olarak değerlendirmek anlamına gelir. Artımlı derleme sırasında hedefler atlanabilir veya Yürütülebilirler, ancak her zaman değerlendirilir. Daha fazla bilgi için bkz. hedef, değerlendirme.

## <a name="target-running"></a>hedef, çalışıyor

False olarak değerlendirilen bir koşula sahip bir hedef çalıştırılmadı, diğer bir deyişle, derleme üzerinde hiçbir etkisi yoktur. Çalıştırılan hedefler yürütülür ya da atlanır. Her iki durumda da hedef değerlendirilir. Daha fazla bilgi için bkz. hedef, değerlendirme.

## <a name="target-skipping"></a>hedef, atlanıyor

Artımlı derleme tüm çıkış dosyalarının güncel olduğunu belirlerse, hedef atlanır, yani hedef değerlendirilir, ancak hedef içindeki görevler yürütülmez. Daha fazla bilgi için bkz. hedef, değerlendirme.

## <a name="target-framework-moniker"></a>hedef çerçeve bilinen adı

Framework tanımlayan bir ad (örneğin,. NETFramework, Silverlight, vb.), sürüm ve hedeflemek istediğiniz profil (Istemci, sunucu vb.).

## <a name="targeting-pack"></a>hedefleme paketi

Belirli bir çerçeve ile dağıtılan derlemelerin listesi ve bu çerçeve için başvuru derlemeleri kümesi.

## <a name="targets-file"></a>Hedef dosya

Hedef dosya, genellikle derlemeyi rehberlik eden hedefleri ve görevleri içeren bir proje dosyasıdır. Kurala göre, *. targets* dosya uzantısına sahiptir. Hedef dosyalar genellikle ilişkili proje dosyalarının sonuna aktarılır.

## <a name="task"></a>görev

Görevler, MSBuild projelerinin derleme işlemlerini gerçekleştirmek için kullandığı yürütülebilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derleyebilir veya bir dış araç çalıştırabilir. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

## <a name="transform"></a>transform

Dönüşüm, bir öğe koleksiyonunun diğerine bire bir dönüştürmedir. Bir dönüştürme, öğe koleksiyonlarını dönüştürmek için bir projenin etkinleştirilmesinin yanı sıra, bir hedefin giriş ve çıkışları arasında doğrudan eşlemeyi belirlemesine olanak sağlar. Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).

## <a name="well-known-metadata"></a>iyi bilinen meta veriler

Bkz. *meta veriler, iyi bilinen*.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
