---
title: MSBuild sözlüğü
description: Derleme altyapısını Microsoft Build Engine bileşenlerini MSBuild terimler (MSBuild) sözlüğü terimlerini öğrenin.
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
ms.openlocfilehash: 3da3236b9d8cef954c4457b5710956751679b059
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085032"
---
# <a name="msbuild-glossary"></a>MSBuild sözlüğü

Bu terimler, Microsoft Build Engine (MSBuild) ve bileşenlerini açıklamak için kullanılır.

## <a name="assemblyfoldersex"></a>AssemblyFoldersEx

Üçüncü taraf satıcıların, tasarım zamanı çözümlemesi başvuru derlemelerini bulmak için bakabilirsiniz desteklemektedir çerçevenin her sürümü için yolları depolar bir kayıt defteri konumu.

## <a name="batching"></a>toplu işleme

Toplu işlem, öğeleri öğe meta verilerine göre *ve* ardından her toplu işi kullanarak bir hedef veya görevi bir kez çalıştırarak, toplu iş olarak bilinen farklı kategorilere bölme anlamına gelir. Toplu işlem, MSBuild for--loop yapısıyla eşdeğerdir. Daha fazla bilgi için bkz. [Toplu işleme.](../msbuild/msbuild-batching.md)

## <a name="build-scope"></a>derleme kapsamı

Derleme kapsamı, MSBuild proje ve çok projeli derlemede oluşturulan tüm alt projeler için görünür olabilecek genel bir özellik gibi bir nesne tanımlar.

## <a name="child-project"></a>alt proje

Bkz. *proje, alt.*

## <a name="condition"></a>Durum

Birçok MSBuild öğeleri koşullu olarak tanımlanabilir; başka bir `Condition` ifadeyle, özniteliği öğesinde görünür. Koşul olarak değerlendirilmediği sürece koşullu öğelerin içeriği `true` yoksayılır. Daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)

## <a name="definition-item"></a>tanım, öğe

Öğe *tanımına bakın.*

## <a name="emit-item"></a>öğe yayma

Derlemenin yürütme aşamasında öğeler, özniteliğine sahip alt öğeleri olan görevler tarafından oluşturulabilir `Output` veya `ItemName` değiştirilebilir. Görevin yeni öğeleri "yayma" olduğu ifade edildi.

## <a name="emit-property"></a>emit özelliği

Derlemenin yürütme aşamasında özellikler, özniteliğine sahip alt öğeleri olan görevler tarafından oluşturulabilir `Output` veya `PropertyName` değiştirilebilir. Görevin yeni özelliği "yayma" olduğu ifade edildi.

## <a name="evaluation-phase"></a>değerlendirme aşaması

Değerlendirme, proje derlemenin ilk aşamasıdır. Tüm özellikler ve öğeler, projede görünme sırasına göre değerlendirilir. İçe aktarılan projeler projede karşılaşıldıklarında değerlendirilir. Hedefler ve görevler, yürütme aşamasına kadar çalıştırılana kadar çalıştırlanmaz ve bildirebilir veya yayacaktır öğeleri değerlendirme sırasında yoksayılır.

## <a name="execution-phase"></a>yürütme aşaması

Yürütme, proje derlemenin ikinci aşamasıdır. Seçilen hedefler yerleşiktir ve görevler işler. Özellikler ve öğeler, değerlendirme değerlerine göre oluşturulabilir veya değiştirilebilir.

## <a name="function-property"></a>işlev, özellik

Bkz. *özellik işlevi.*

## <a name="function-item"></a>işlev, öğe

Bkz. öğe işlevi.

## <a name="item"></a>öğe

Öğeler derleme sistemine girişlerdir ve öğe adlarına göre öğe türlerine gruplandı. Öğeler genellikle dosyaları temsil ediyor. Öğeler ait olduğu öğe türüne göre adlandırılmış olduğundan öğe *ve* *öğe değeri* terimleri birbirinin yerine kullanılabilir. Daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md)

## <a name="item-definition"></a>öğe tanımı

Öğe tanımı grupları, herhangi bir öğe türüne varsayılan meta veriler ekli öğe tanımları içerir. İyi bilinen meta veriler gibi varsayılan meta veriler de belirtilen öğe türünün tüm öğeleriyle ilişkilendirilmektedir. Varsayılan meta veriler bir öğe tanımında açıkça geçersiz kılınabilir. Daha fazla bilgi için [bkz. Öğe tanımları.](../msbuild/item-definitions.md)

## <a name="item-function"></a>item işlevi

Öğe işlevleri, projedeki öğeler hakkında bilgi sağlar. Bu işlevler Distinct() öğelerini alma sürecini basitleştirir ve öğelerde döngüye almaya göre daha hızlıdır. Öğe yollarını ve dizelerini işlemek için işlevler vardır. Daha fazla bilgi için bkz. [Öğe işlevleri.](../msbuild/item-functions.md)

## <a name="item-metadata"></a>öğe meta verileri

Bkz. *meta veriler, öğe.*

## <a name="item-type"></a>öğe türü

Öğe türleri, görevler için parametre olarak kullanılan öğelerin adlandırılmış listeleridir. Görevler, derleme işleminin adımlarını gerçekleştirmek için öğe değerlerini kullanır. Daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md)

## <a name="metadata-item"></a>meta veriler, öğe

Öğe meta verileri, bir öğeyle ilişkili ad-değer çiftleri koleksiyonudur. Meta veriler öğe için açıklayıcı bilgiler sağlar ve iyi bilinen meta veriler dışında isteğe bağlıdır. Daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md)

## <a name="metadata-well-known"></a>meta veriler, iyi bilinen

İyi bilinen meta veriler, önceden tanımlanmış bir değer kullanılarak başlatılan salt okunur öğe meta verileridir. İyi bilinen meta veriler, bir dosyaya başvurulan öğe için açıklayıcı bilgiler sağlar. Örneğin, adlı iyi bilinen meta verilerin `FullPath` değeri, başvurulan dosyanın tam yoludur. Daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md)

## <a name="multitargeting"></a>çoklu sürüm desteği

Bir uygulama veya derleme projesinin, MSBuild'den ve Visual Studio.

## <a name="profile"></a>profil

Tam çerçevenin bir alt kümesi. Bu, bir makineye indirilmesi gereken miktarı en aza indirmek için kullanılır.

## <a name="project-file"></a>proje dosyası

Proje dosyası, derlemeyi MSBuild betiği içerir. Project genellikle *.csproj veya .vbproj* gibi *proj* ile sona eren bir *dosya uzantısına sahip olur.* Project dosyaları, özellik dosyalarını ve hedef dosyaları içeri aktarabilirsiniz.

## <a name="property"></a>özellik

Özellik, derleme işlemini kontrol etmek için kullanılan bir anahtar-değer çiftidir. Daha fazla bilgi için [bkz. MSBuild .](../msbuild/msbuild-properties.md)

## <a name="property-environment"></a>özellik, ortam

Ortam özelliği, aynı adı alan bir sistem ortam değişkeninin değerine otomatik olarak başlatılan bir özelliktir. Daha fazla bilgi için [bkz. MSBuild .](../msbuild/msbuild-properties.md)

## <a name="property-file"></a>özellik dosyası

Özellik dosyası, çoğu özellik gruplarını ve derlemeye kılavuz olan öğe gruplarını içeren bir proje dosyasıdır. Kural gereği , *.props dosya uzantısına sahip olur.* Özellik dosyaları genellikle ilişkili proje dosyalarının başında içe aktarılır.

## <a name="property-function"></a>property, function

Özellik işlevi, betikleri değerlendirmek için kullanılan bir sistem özelliği MSBuild yöntemidir. Özellik yöntemleri, sistem zamanını okumak, dizeleri karşılaştırmak, normal ifadelerle eşleşmek ve diğer eylemleri gerçekleştirmek için kullanılabilir. Daha fazla bilgi için [bkz. Özellik işlevleri.](../msbuild/property-functions.md)

## <a name="property-function-nested"></a>property işlevi, iç içe geçmiş

Özellik işlevleri daha karmaşık işlevler oluşturmak için birleştirilmiş olabilir. Örneğin,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Daha fazla bilgi için [bkz. Özellik işlevleri.](../msbuild/property-functions.md)

## <a name="property-global"></a>özellik, genel

Genel özellik, derleme işlemini kontrol etmek için kullanılan bir anahtar-değer çiftidir. Genel özellikler bir komut isteminde veya bir MSBuild görevinin özniteliği kullanılarak ayarlanır ve derlemenin `Properties` değerlendirme aşamasında değiştirilemez. [](../msbuild/msbuild-task.md) Daha fazla bilgi için [bkz. MSBuild .](../msbuild/msbuild-properties.md)

## <a name="property-local"></a>Özellik, yerel

Yerel bir özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Bu terim yalnızca genel özellik olmayan bir özelliği ayırt etmek için kullanılır.

## <a name="property-registry"></a>Özellik, kayıt defteri

Bir kayıt defteri özelliğinin bir sistem kayıt defteri alt anahtarının değerini okuyan özel bir sözdizimi kullanılarak ayarlanan bir değeri vardır. daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="property-reserved"></a>Özellik, ayrılmış

Ayrılmış bir özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Ayrılmış Özellikler otomatik olarak önceden tanımlanmış değerler olarak başlatılır. daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="project-scope"></a>Proje kapsamı

Project kapsam, yalnızca içeren proje dosyasında ve içeri aktardığı herhangi bir projede görünür olan yerel bir özellik gibi bir MSBuild nesnesini tanımlar.

## <a name="project-child"></a>Proje, alt öğe

bir proje derlemesi sırasında MSBuild görevi tarafından bir alt proje oluşturulur. bu yeni proje, MSBuild görevini içeren hedefi içeren veya içeri aktaran projenin bir alt öğesidir. Alt proje, öznitelik tarafından değiştirilmedikleri takdirde üst projenin genel özelliklerini devralır `Properties` .

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

görevler, MSBuild projelerin derleme işlemleri gerçekleştirmek için kullandığı çalıştırılabilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derleyebilir veya bir dış araç çalıştırabilir. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

## <a name="transform"></a>transform

Dönüşüm, bir öğe koleksiyonunun diğerine bire bir dönüştürmedir. Bir dönüştürme, öğe koleksiyonlarını dönüştürmek için bir projenin etkinleştirilmesinin yanı sıra, bir hedefin giriş ve çıkışları arasında doğrudan eşlemeyi belirlemesine olanak sağlar. Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).

## <a name="well-known-metadata"></a>iyi bilinen meta veriler

Bkz. *meta veriler, iyi bilinen*.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
