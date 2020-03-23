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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633349"
---
# <a name="msbuild-glossary"></a>MSBuild sözlüğü

Bu terimler, Microsoft Build Engine (MSBuild) ve bileşenlerini tanımlamak için kullanılır.

## <a name="glossary"></a>Sözlük

AssemblyFoldersEx\
Üçüncü taraf satıcıların, tasarım süresi çözümlemesi referans derlemeleri bulmak için bakabilecekleri çerçevenin destekledikleri her sürümü için yollar depoladıkları bir kayıt defteri konumu.

toplu iş\
Toplu İşlem, maddeleri madde meta verilerine göre *toplu iş*olarak bilinen farklı kategorilere bölmek ve her bir toplu iş parçasını kullanarak bir hedefi veya görevi bir kez çalıştırmak anlamına gelir. Toplu İşlem, for-loop yapısının MSBuild eşdeğeridir. Daha fazla bilgi için [Toplu İşlem'e](../msbuild/msbuild-batching.md)bakın.

yapı kapsamı\
Yapı kapsamı, örneğin, bir proje ve çoklu proje yapısında oluşturulan tüm alt projeler tarafından görülebilir bir genel özellik olan bir MSBuild nesnesini açıklar.

çocuk projesi\
*Projeye bak, çocuk.*

durum\
Birçok MSBuild öğesi koşullu olarak tanımlanabilir; diğer bir `Condition` deyişle, öznitelik öğede görünür. Koşullu öğelerin içeriği, koşul değerlendirilmesi `true`sürece yoksayılır. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.

tanım, öğe\
*Madde tanımına*bakın.

öğeyi yayıyorum\
Yapının yürütme aşamasında, öğeler özniteliği olan `Output` `ItemName` alt öğeleri olan görevler tarafından oluşturulabilir veya değiştirilebilir. Görevin yeni öğeleri "yayıştırmak" olduğu söylenir.

özellik yayıyorum\
Yapının yürütme aşamasında, özellikler öznitelik sahibi `Output` `PropertyName` alt öğeleri olan görevler tarafından oluşturulabilir veya değiştirilebilir. Görevin yeni mülkü "yayıştırmak" olduğu söylenir.

değerlendirme aşaması\
Değerlendirme, proje oluşturmanın ilk aşamasıdır. Tüm özellikler ve öğeler projede göründükleri sırada değerlendirilir. İthal edilen projeler, projede karşılaşılan gibi değerlendirilir. Hedefler ve görevler yürütme aşamasına kadar çalıştırılmez ve beyan ettikleri veya yayacakları özellikler veya öğeler değerlendirme sırasında yoksayılır.

yürütme aşaması\
Yürütme, proje oluşturmanın ikinci aşamasıdır. Seçili hedefler oluşturulur ve görevler çalıştırılır. Özellikler ve öğeler, değerlendirme değerlerine göre oluşturulabilir veya değiştirilebilir.

fonksiyonu, özellik\
*Bkz. özellik işlevi.*

fonksiyonu, öğe\
Madde işlevine bakın.

öğe\
Öğeler yapı sistemine girer ve öğe adlarına göre madde türlerine gruplanır. Öğeler genellikle dosyaları temsil. Maddeler ait oldukları madde türüne göre adlandırıldıklarına göre, *terimler madde* ve *madde değeri* birbirinin yerine kullanılabilir. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.

madde tanımı\
Madde tanım grupları, herhangi bir madde türüne varsayılan meta veri ekleyen madde tanımları içerir. İyi bilinen meta veriler gibi, varsayılan meta veriler de belirtilen madde türünün tüm öğeleriyle ilişkilidir. Varsayılan meta veriler, madde tanımında açıkça geçersiz kılınabilir. Daha fazla bilgi için [Madde tanımlarına](../msbuild/item-definitions.md)bakın.

öğe fonksiyonu\
Öğe işlevleri projedeki öğeler hakkında bilgi alır. Bu işlevler Distinct() öğelerini almayı kolaylaştırır ve öğeler arasında döngü yapmaktan daha hızlıdır. Öğe yollarını ve dizeleri işlemek için işlevler vardır. Daha fazla bilgi için [Öğe işlevlerine](../msbuild/item-functions.md)bakın.

öğe meta data\
Bkz. *meta veriler, öğe*.

öğe türü\
Madde türleri, görevler için parametre olarak kullanılabilecek öğelerin listeleri olarak adlandırılır. Görevler, yapı işleminin adımlarını gerçekleştirmek için madde değerlerini kullanır. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.

meta veri, öğe\
Madde meta verileri, bir öğeyle ilişkili ad değeri çiftleri topluluğudur. Meta veriler öğe için açıklayıcı bilgiler sağlar ve iyi bilinen meta veriler dışında isteğe bağlıdır. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.

meta veriler, iyi bilinen\
İyi bilinen meta veriler, önceden tanımlanmış bir değer kullanılarak başharfe bürünen salt okunur öğe meta verileridir. İyi bilinen meta veriler, dosyaya başvuran bir öğe için açıklayıcı bilgiler sağlar. Örneğin, tanınmış meta verilerin değeri başvurulan `FullPath` dosyanın tam yoludur. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.

çoklu hedefleme\
MsBuild ve Visual Studio birçok farklı CLR ve çerçeveleri hedef bir uygulama veya montaj projesi için yeteneği.

profili\
Tam çerçevenin bir alt kümesi. Bu, bir makineye karşıdan yüklenmeleri gereken miktarı en aza indirmek için kullanılır.

proje dosyası\
Proje dosyası, yapıyı denetleyen MSBuild komut dosyası içerir. Proje dosyaları genellikle *proj*ile biten bir dosya uzantısı var , *.csproj* veya *.vbproj*gibi . Proje dosyaları özellik ve hedef dosyaları içe aktarabilir.

özellik\
Özellik, yapı işlemini denetlemek için kullanılan anahtar değer çiftidir. Daha fazla bilgi için [MSBuild özelliklerine](../msbuild/msbuild-properties.md)bakın.

mülkiyet, çevre\
Ortam özelliği, aynı ada sahip bir sistem ortamı değişkeninin değerine otomatik olarak başharflenen bir özelliktir. Daha fazla bilgi için [MSBuild özelliklerine](../msbuild/msbuild-properties.md)bakın.

özellik dosyası\
Özellik dosyası, çoğunlukla özellik grupları ve yapıya kılavuz öğe gruplarını içeren bir proje dosyasıdır. Sözleşmeye göre, bu dosya uzantısı *.props*vardır. Özellik dosyaları genellikle ilişkili proje dosyalarının başında alınır.

özellik, fonksiyon\
Özellik işlevi, MSBuild komut dosyalarını değerlendirmek için kullanılabilecek bir sistem özelliği veya yöntemidir. Özellik yöntemleri, sistem zamanını okumak, dizeleri karşılaştırmak, normal ifadeleri eşleştirmek ve diğer eylemleri gerçekleştirmek için kullanılabilir. Daha fazla bilgi için [Bkz. Özellik işlevleri.](../msbuild/property-functions.md)

özellik fonksiyonu, iç içe\
Özellik işlevleri daha karmaşık işlevler oluşturmak için birleştirilebilir. Örneğin,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Daha fazla bilgi için [Bkz. Özellik işlevleri.](../msbuild/property-functions.md)

mülkiyet, küresel\
Genel özellik, yapı işlemini denetlemek için kullanılan anahtar değer çiftidir. Genel özellikler komut isteminde veya BIR `Properties` [MSBuild görevinin](../msbuild/msbuild-task.md)özniteliği kullanılarak ayarlanır ve yapının değerlendirme aşamasında değiştirilemez. Daha fazla bilgi için [MSBuild özelliklerine](../msbuild/msbuild-properties.md)bakın.

özellik, yerel\
Yerel özellik, yapı işlemini denetlemek için kullanılan anahtar değer çiftidir. Bu terim yalnızca genel bir özellik olmayan bir özelliği ayırt etmek için kullanılır.

mülkiyet, kayıt defteri\
Kayıt defteri özelliği, sistem kayıt defteri alt anahtarının değerini okuyan özel bir sözdizimi kullanılarak ayarlanan bir değere sahiptir. Daha fazla bilgi için [MSBuild özelliklerine](../msbuild/msbuild-properties.md)bakın.

mülkiyet, ayrılmış\
Ayrılmış özellik, yapı işlemini denetlemek için kullanılan anahtar değer çiftidir. Ayrılmış özellikler otomatik olarak önceden tanımlanmış değerlere başolarak başlanır. Daha fazla bilgi için [MSBuild özelliklerine](../msbuild/msbuild-properties.md)bakın.

proje kapsamı\
Proje kapsamı, yalnızca içeren proje dosyasında ve içe aktardığı tüm projelerde görülebilen bir MSBuild nesnesini (örneğin, yerel bir özellik) açıklar.

proje, çocuk\
Bir alt proje, proje oluşturma sırasında MSBuild görevi tarafından oluşturulur. Bu yeni proje, MSBuild görevini içeren hedefi içeren veya içe alan projenin bir alt nedenidir. Öznitelik tarafından `Properties` değiştirilmediği sürece, alt proje ana projenin genel özelliklerini devralır.

redist listesi\
Yeniden dağıtım listesi: belirli bir çerçeveye karşılık gelen derlemeler listesi.

referans derleme\
Bir uygulama oluşturmak için tasarım süresi içinde kullanılan bir derleme. Bir başvuru derlemesi, gerçek kodu ve özel arabirimleri ondan kaldırarak yalnızca meta verileri ve ortak arabirimleri bırakabilir.

kayıt özelliği\
Bkz. *mülkiyet, kayıt defteri.*

hedef\
Hedef, görevleri belirli bir sırada gruplaştırır ve proje dosyasının bölümlerini yapı işlemine giriş noktası olarak ortaya çıkarır. Daha fazla bilgi için [Bkz. Hedefler.](../msbuild/msbuild-targets.md)

hedef, bina\
Hedefe bak, koşuyor.

hedef, değerlendirme\
Artımlı derleme nedeniyle, hedefler özellikleri ve öğeleri olası değişiklikler için analiz edilmelidir. Hedef atlansa bile, bu değişiklikler yapılmalıdır. Bir hedefi değerlendirmek, bu çözümlemesi gerçekleştirmek ve bu değişiklikleri yapmak anlamına gelir. Daha fazla bilgi için [Bkz. Artımlı yapılar.](../msbuild/incremental-builds.md)

hedef, yürütme\
Bir hedefi yürütmek, hedefi değerlendirmek ve koşulsuz veya koşulları doğru olarak değerlendirilen tüm görevleri yürütmek anlamına gelir. Artımlı derleme sırasında, hedefler atlanabilir veya yürütülebilir, ancak her zaman değerlendirilir. Daha fazla bilgi için, hedef, değerlendirme bakın.

hedef, çalışan\
Yanlışı değerlendiren bir koşula sahip bir hedef çalıştırılmez, yani yapı üzerinde hiçbir etkisi yoktur. Çalıştırılan hedefler yürütülür veya atlanır. Her iki durumda da hedef değerlendirilir. Daha fazla bilgi için, hedef, değerlendirme bakın.

hedef, atlama\
Artımlı derleme tüm çıktı dosyalarının güncel olduğunu belirlerse, hedef atlanır, yani hedef değerlendirilir, ancak hedef içindeki görevler yürütülmez. Daha fazla bilgi için, hedef, değerlendirme bakın.

hedef çerçeve lakabı\
Çerçeveyi açıklayan bir ad (örneğin. NETFramework, Silverlight, vb. sürüm ve hedeflemek istediğiniz profil (İstemci, Sunucu, vb.)

hedefleme paketi\
Belirli bir çerçeveyle dağıtılan derlemelerin listesi ve bu çerçeve için başvuru derlemeleri kümesi.

hedefler dosyası\
Hedefler dosyası, çoğunlukla hedefleri ve yapıyı yönlendiren görevleri içeren bir proje dosyasıdır. Sözleşmeye göre, dosya uzantısı *.targets*vardır. Hedef dosyalar genellikle ilişkili proje dosyalarının sonunda alınır.

görev\
Görevler, MSBuild projelerinin yapı işlemleri gerçekleştirmek için kullandığı yürütülebilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derleyebilir veya harici bir araç çalıştırabilir. Daha fazla bilgi için [Görevler'e](../msbuild/msbuild-tasks.md)bakın.

dönüştürme\
Dönüştürme, bir öğe koleksiyonunun diğerine bire bir dönüştürülmesidir. Bir projenin madde koleksiyonlarını dönüştürmesini etkinleştirmeye ek olarak, dönüştürme, bir hedefin girdi ve çıktıları arasında doğrudan eşleme tanımlamasını sağlar. Daha fazla bilgi için [Transforms'a](../msbuild/msbuild-transforms.md)bakın.

iyi bilinen meta veriler\
Bkz. *meta veriler, iyi bilinen.*

## <a name="see-also"></a>Ayrıca bkz.

- [Msbuild](../msbuild/msbuild.md)
