---
title: MSBuild sözlüğü
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f20fdb4cd809e422bc33535f3143b45db99842f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633349"
---
# <a name="msbuild-glossary"></a>MSBuild sözlüğü

Bu terimler Microsoft Build Engine (MSBuild) ve bileşenlerini tanımlamakta kullanılır.

## <a name="glossary"></a>Sözlük

AssemblyFoldersEx\
Üçüncü taraf satıcıların, tasarım zamanı çözümlemenin başvuru derlemelerini bulmak için nerede görünebileceği, desteklediği her bir sürüm için yolları depolayacağı bir kayıt defteri konumu.

işlem\
Toplu işleme öğeleri, öğe meta verileri temelinde *toplu*iş olarak bilinen farklı kategorilere bölmek ve sonra her toplu işi kullanarak bir kez hedef veya görev çalıştırmak anlamına gelir. Toplu işleme, for--Loop yapısının MSBuild eşdeğeridir. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.

Yapı kapsamı\
Yapı kapsamı, bir proje için ve çok projeli bir derlemede oluşturulan herhangi bir alt proje için görünebilir olan genel bir özellik gibi bir MSBuild nesnesini tanımlar.

alt proje\
Bkz. *Proje, alt*.

koşul\
Birçok MSBuild öğesi koşullu olarak tanımlanabilir; diğer bir deyişle, `Condition` özniteliği öğesinde görüntülenir. Koşul `true`olarak değerlendirilmediği takdirde koşullu öğelerin içeriği yoksayılır. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).

Tanım, öğe\
*Öğe tanımına*bakın.

öğeyi yay\
Bir yapılandırmanın yürütme aşamasında öğeler, `ItemName` özniteliğine sahip alt öğe `Output` öğeleri olan görevler tarafından oluşturulabilir veya değiştirilebilir. Görev, yeni öğeleri "yayma" olarak kabul edilir.

özelliği göster\
Bir yapı yürütme aşamasında, Özellikler `PropertyName` özniteliğine sahip alt öğe `Output` olan görevler tarafından oluşturulabilir veya değiştirilebilir. Görev, yeni özelliği "yayma" olarak kabul edilir.

değerlendirme aşaması\
Değerlendirme, proje derlemesinin ilk aşamasıdır. Tüm özellikler ve öğeler, projede göründükleri sırayla değerlendirilir. İçeri aktarılan projeler, projede karşılaştığı şekilde değerlendirilir. Hedefler ve görevler, yürütme aşamasına kadar çalışmaz ve bildirildikleri ya da yayma işlemleri değerlendirme sırasında yok sayılır.

yürütme aşaması\
Yürütme, proje derlemesinin ikinci aşamasıdır. Seçilen hedefler oluşturulur ve görevler çalıştırılır. Özellikler ve öğeler, değerlendirme değerleriyle karşılaştırıldığında oluşturulabilir veya değiştirilebilir.

işlev, özellik\
Bkz. *Özellik işlevi*.

işlev, öğe\
Bkz. öğe işlevi.

maddesinin
Öğeler, derleme sistemine giriş ve öğe adlarına göre öğe türlerine göre gruplandırılır. Öğeler genellikle dosyaları temsil eder. Öğeler ait oldukları öğe türüne göre adlandırıldıklarından, hüküm *öğesi* ve *öğe değeri* birbirlerinin yerine kullanılabilir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

öğe tanımı\
Öğe tanımı grupları herhangi bir öğe türüne varsayılan meta veri ekleyen öğe tanımlarını içerir. İyi bilinen meta veriler gibi, varsayılan meta veriler belirtilen öğe türünün tüm öğeleriyle ilişkilendirilir. Varsayılan meta veriler, bir öğe tanımında açıkça geçersiz kılınabilir. Daha fazla bilgi için bkz. [öğe tanımları](../msbuild/item-definitions.md).

öğe işlevi\
Öğe işlevleri, projedeki öğeler hakkında bilgi alır. Bu işlevler ayrı () öğeleri almayı basitleştirir ve öğeler aracılığıyla döngüden daha hızlıdır. Öğe yollarını ve dizeleri işlemek için işlevler vardır. Daha fazla bilgi için bkz. [öğe işlevleri](../msbuild/item-functions.md).

öğe meta verileri\
Bkz. *meta veriler, öğe*.

öğe türü \
Öğe türleri, görevler için parametre olarak kullanılabilecek öğelerin adlandırılmış listeleridir. Görevler, yapı işleminin adımlarını gerçekleştirmek için öğe değerlerini kullanır. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

meta veri, öğe \
Öğe meta verileri bir öğeyle ilişkili ad-değer çiftleri koleksiyonudur. Meta veriler, öğe için açıklayıcı bilgiler sağlar ve iyi bilinen meta veriler dışında isteğe bağlıdır. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

meta veriler, iyi bilinen \
İyi bilinen meta veriler önceden tanımlanmış bir değer kullanılarak başlatılan salt okunurdur. İyi bilinen meta veriler, bir dosyaya başvuran bir öğe için açıklayıcı bilgiler sağlar. Örneğin, `FullPath` adlı iyi bilinen meta verilerin değeri, başvurulan dosyanın tam yoludur. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

çoklu sürüm desteği
Bir uygulama veya derleme projesinin, MSBuild 'den ve Visual Studio 'dan birçok farklı CLR 'nin ve çerçevesini hedefleyebilme özelliği.

profilinizi
Tam Framework 'ün bir alt kümesi. Bu, bir makineye indirilmesi gereken miktarı en aza indirmek için kullanılır.

Proje dosyası \
Proje dosyası, derlemeyi denetleyen MSBuild betiğini içerir. Proje dosyaları genellikle *. csproj* veya *. vbproj*gibi *proj*ile biten bir dosya uzantısına sahiptir. Proje dosyaları, özellik dosyalarını ve hedef dosyaları içeri aktarabilir.

özelliði
Özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

Özellik, ortam \
Ortam özelliği, aynı ada sahip bir sistem ortam değişkeninin değerine otomatik olarak başlatılan bir özelliktir. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

Özellik dosyası \
Özellik dosyası, derleme kılavuzunu oluşturan genellikle özellik gruplarını ve öğe gruplarını içeren bir proje dosyasıdır. Kurala göre, *. props*dosya uzantısına sahiptir. Özellik dosyaları genellikle ilişkili proje dosyalarının başlangıcında içeri aktarılır.

Özellik, işlev \
Özellik işlevi, MSBuild betiklerini değerlendirmek için kullanılabilen bir sistem özelliğidir veya yöntemidir. Özellik yöntemleri, sistem saatini okumak, dizeleri karşılaştırmak, normal ifadelerle eşleştirmek ve diğer işlemleri gerçekleştirmek için kullanılabilir. Daha fazla bilgi için bkz. [özellik işlevleri](../msbuild/property-functions.md).

Özellik işlevi, iç içe geçmiş \
Özellik işlevleri, daha karmaşık işlevler oluşturmak için birleştirilebilir. Örneğin,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Daha fazla bilgi için bkz. [özellik işlevleri](../msbuild/property-functions.md).

Özellik, Genel \
Genel özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Genel Özellikler bir komut isteminde veya bir [MSBuild görevinin](../msbuild/msbuild-task.md)`Properties` özniteliği kullanılarak ayarlanır ve bir yapılandırmanın değerlendirme aşamasında değiştirilemez. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

Özellik, yerel \
Yerel bir özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Bu terim yalnızca genel özellik olmayan bir özelliği ayırt etmek için kullanılır.

Özellik, kayıt defteri \
Bir kayıt defteri özelliğinin bir sistem kayıt defteri alt anahtarının değerini okuyan özel bir sözdizimi kullanılarak ayarlanan bir değeri vardır. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

Özellik, ayrılmış \
Ayrılmış bir özellik, yapı işlemini denetlemek için kullanılan bir anahtar-değer çiftidir. Ayrılmış Özellikler otomatik olarak önceden tanımlanmış değerler olarak başlatılır. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

Proje-kapsam \
Proje kapsamı, örneğin, yalnızca içeren proje dosyasında ve içeri aktardığı herhangi bir projede görünür olan yerel bir özellik gibi bir MSBuild nesnesini tanımlar.

Proje, alt öğe \
Bir alt proje, proje derlemesi sırasında MSBuild görevi tarafından oluşturulur. Bu yeni proje, MSBuild görevini içeren hedefi içeren veya içeri aktaran projenin bir alt öğesidir. Alt proje, `Properties` özniteliği tarafından değiştirilmedikleri takdirde üst projenin genel özelliklerini devralır.

Redist listesi \
Yeniden dağıtım listesi: belirli bir çerçeveye karşılık gelen derlemelerin listesi.

başvuru derlemesi \
Tasarım zamanı sırasında bir uygulama oluşturmak için kullanılan bir derleme. Bir başvuru derlemesi, gerçek kod ve özel arabirimlerin kaldırılmasına ve yalnızca meta verileri ve genel arabirimleri terk edebilir.

kayıt defteri özelliği \
Bkz. *özellik, kayıt defteri*.

hedef
Hedef, görevleri belirli bir sırada gruplandırır ve proje dosyasının bölümlerini yapı işlemine giriş noktası olarak gösterir. Daha fazla bilgi için bkz. [hedefler](../msbuild/msbuild-targets.md).

hedef, derleme \
Bkz. hedef, çalışıyor.

hedef, değerlendirme \
Artımlı derleme nedeniyle, hedefler Özellikler ve öğelerde olası değişiklikler için çözümlenmelidir. Hedef atlansa bile, bu değişikliklerin yapılması gerekir. Bir hedefin değerlendirilmesi, bu çözümlemenin gerçekleştirilmesi ve bu değişikliklerin yapılması anlamına gelir. Daha fazla bilgi için bkz. [Artımlı derlemeler](../msbuild/incremental-builds.md).

hedef, yürütülüyor \
Bir hedefin yürütülmesi, bir koşulu değerlendirmek ve koşulsız tüm görevleri yürütmek ya da koşullarını doğru olarak değerlendirmek anlamına gelir. Artımlı derleme sırasında hedefler atlanabilir veya Yürütülebilirler, ancak her zaman değerlendirilir. Daha fazla bilgi için bkz. hedef, değerlendirme.

hedef, çalışıyor \
False olarak değerlendirilen bir koşula sahip bir hedef çalıştırılmadı, diğer bir deyişle, derleme üzerinde hiçbir etkisi yoktur. Çalıştırılan hedefler yürütülür ya da atlanır. Her iki durumda da hedef değerlendirilir. Daha fazla bilgi için bkz. hedef, değerlendirme.

hedef, atlanıyor \
Artımlı derleme tüm çıkış dosyalarının güncel olduğunu belirlerse, hedef atlanır, yani hedef değerlendirilir, ancak hedef içindeki görevler yürütülmez. Daha fazla bilgi için bkz. hedef, değerlendirme.

hedef çerçeve bilinen adı \
Framework tanımlayan bir ad (örneğin,. NETFramework, Silverlight, vb.), sürüm ve hedeflemek istediğiniz profil (Istemci, sunucu vb.).

hedeflenen paket \
Belirli bir çerçeve ile dağıtılan derlemelerin listesi ve bu çerçeve için başvuru derlemeleri kümesi.

Hedef dosya \
Hedef dosya, genellikle derlemeyi rehberlik eden hedefleri ve görevleri içeren bir proje dosyasıdır. Kurala göre, *. targets*dosya uzantısına sahiptir. Hedef dosyalar genellikle ilişkili proje dosyalarının sonuna aktarılır.

görevinin
Görevler, MSBuild projelerinin derleme işlemlerini gerçekleştirmek için kullandığı yürütülebilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derleyebilir veya bir dış araç çalıştırabilir. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

Dönüşümler
Dönüşüm, bir öğe koleksiyonunun diğerine bire bir dönüştürmedir. Bir dönüştürme, öğe koleksiyonlarını dönüştürmek için bir projenin etkinleştirilmesinin yanı sıra, bir hedefin giriş ve çıkışları arasında doğrudan eşlemeyi belirlemesine olanak sağlar. Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).

iyi bilinen meta veriler \
Bkz. *meta veriler, iyi bilinen*.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
