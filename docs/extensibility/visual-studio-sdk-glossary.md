---
title: Visual Studio SDK sözlüğü | Microsoft Docs
description: bu sözlük Visual Studio SDK belgelerinde kullanılan terimler için tanımlar sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 78a66998e18ef68afe71e51f8d7ce99c7a75fc3a
ms.sourcegitcommit: 1c0eda2db1b1fff9595ca644503f467bf3e223e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "137094904"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK sözlüğü
Bu sözlük, belgelerde kullanılan terimlere yönelik tanımlar sağlar [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] .

## <a name="terms"></a>Terimler

**eklenti**  
Bir yardımcı program uygulaması, sürücü veya bir birincil uygulamaya eklenen diğer yazılımlar. Visual Studio tümleşik geliştirme ortamında (ıde), eklenti ıde 'nin yeteneklerini genişleten otomasyon tabanlı bir uygulamadır.

**otomatikleştirme modeli**  
genişletilebilirlik modeli olarak Visual Studio önceki sürümlerinde bilinen otomasyon modeli, ıde 'yi hedefleyen temel yordamlara erişmenizi sağlayan bir programlama arabirimidir. Eklentiler, sihirbazlar ve makrolar, IDE 'nin işlevselliğini denetlemek veya genişletmek için Otomasyon modelindeki nesneleri kullanır.

**komut UI bağlamı**  
Bir GUID 'in, bir kullanıcı arabirimi komutunun veya bir araç çubuğu gibi bir öğenin görünürlüğiyle ilişkilendirilmesi. Komut UI bağlamı, bir pencereye eklenmemiş olan seçim bağlamından farklı.

Komut UI bağlamı şu şekilde kullanılabilir:
- Belirli bir pencere etkinleştirildiğinde görüntülenen bir araç çubuğuna GUID atayın.
- Bir VSPackage yüklemesine veya çalıştırmaya gerek kalmadan bir komutun kullanılabilirliğine bir GUID atayın.
- Etkin anahtar bağlamasını etkilemek için bir GUID atayın.
- Makro kaydını açmak için bir GUID atayın.
- Hata ayıklama modunu etkinleştirmek veya bir düzenleyicide tasarım ve çalıştırma modu arasında geçiş yapmak için bir GUID atayın.

**bileşeninde**  
Uygulamanın, yazılımın uygulamasıyla ilgili önceden mevcut herhangi bir bilgi sahibi olmadan, uygulamanın işlevselliğinin bir parçası haline getirilebilir yazılım parçası. Bir bileşen ile uygulama arasındaki iletişim yalnızca OLE stil arabirimleri aracılığıyla yapılır.

**Bileşen Yöneticisi**  
`SOleComponentManager`En üst düzey bileşenlere yönelik kullanıcı arabirimi koordinasyon hizmetleri sağlayan bir hizmet. `SOleComponentManager`Hizmet, arabirimini uygular `IOleComponentManager` .

**bileşen Kullanıcı Arabirimi Yöneticisi**  
`SOleComponentUIManager`Kullanıcı arabirimi koordinasyon hizmetleri sağlayan bir hizmet. `SOleComponentUIManager`Hizmet, `IOleComponentUIManager` ve arabirimlerini uygular `IOleInPlaceComponentUIManager` .

**bağlam paketi**  
`IVsUserContext`Ortam bileşenine eklenmiş bir nesne (com nesnesi). Bu nesne, bileşenle ilgili arama anahtar sözcüklerini, **F1** anahtar sözcüklerini ve öznitelikleri barındırır. Bağlam paketleri buna bağlı olan herhangi bir alt bağlam torbaya işaret edilir.

**bağlam sağlayıcısı**  
IDE içinde kendisiyle ilişkili bir bağlam paketi olan bir bileşen. Bu tür bileşenler bir araç penceresi, düzenleyici veya proje hiyerarşisi içerir.

**Layana**  
Kullanıcıların UI (formlar, düğmeler ve diğer denetimler) öğelerini işlemesini sağlayan bir programlama arabirimi.

**DocData**  
Belge/görünüm ayrımı (örneğin, metin düzenleyici durumunda, bu, tüm metin Düzenleyicisi görünümlerini temel alan metin arabelleği) olan bir dünyanın temel verilerini kapsayan bir COM nesnesi. EditorFactory bu nesneyi sağlayamazsa, IDE onun adına bir tane oluşturmaz. Bu nesnenin sorumluluğu, aynı şekilde birden fazla görünüm için veri kalıcılığını ve paylaşım semantiğini yönettiğdedir `DocData` . `DocData`Nesne `IOleCommandTarget` arabirimini destekliyorsa, UIShell komut yönlendirmesine dahil edilir.

**DocObject**  
Kullanıcı arabirimini konak tarafından sunulan bir çerçeve içinde barındırmak için kullanılan teknoloji. Daha belirgin olarak, bu terim ve ilgili arabirimleri destekleyen herhangi bir eklemeye başvurur `IOleDocument` . bu teknoloji, COM belgelerinin uygulama ayrıntısı, Visual Basic 5,0 ' deki araç pencereleri, Visual Basic 6,0 ' deki ActiveX tasarımcıları vb. gibi birçok olası uygulamayı içerir.

**belge**  
Bir bütün olarak belgeye genel olarak başvurmak için kullanılır — `DocData` ve `DocView` . Örneğin, bir Belgebir çerçeve bir içerir `DocView` , ancak kalıcılığı işlemek için öğesine bir başvurusu da saklar `DocData` .

**DocView**  
Kullanıcının temel olarak görüntülemek ve işlemek için etkileşimde bulunduğu DocObject/katıştırma/WindowPane `DocData` . Kullanıcılar, arabirim tasarımının parçası olan belge/görünüm ayrımı özelliğinden faydalanır `DocObject` . Kullanıcılar, olarak bilinen temel alınan verilerin daha soyut (ve daha az şekillendirilmiş) bir kavramı kullanmak yerine bir görünüm görevi gören bir tüm DocObject kullanır `DocData` . `DocView` nesneler, IDE 'nin belge çerçevesi nesneleriyle (MDI alt pencereleri) her zaman katıştırılır.

**MIÞTIR**  
`DTE`(geliştirme araçları genişletilebilirliği) nesnesi, ıde 'yi programlama yoluyla otomatik hale getirmenizi ve genişletmenizi sağlayan Visual Studio automation modelindeki en üst erişim noktasıdır.

**Dinamik Yardım penceresi**  
IDE tarafından uygulanan ve arama anahtar sözcüğü veya **F1** yardım konuları listesini görüntüleyen araç penceresi.

**düzenleyen**  
Öğesini uygulayan kod (sınıf, CLSID) `DocView` . Ayrıca `DocData` Görünüm ve veri ayrımı destekleniyorsa de uygular.

**uzantının**  
IDE 'ye değiştiren, özelleştiren veya ekleyen bir özellik. Otomasyon modeli veya VSPackages kullanarak uzantılar oluşturursunuz.

**Dış düzenleyici**  
IDE 'ye özgü olmayan, Microsoft Word gibi bir düzenleyici. Kendi mekanizmaları aracılığıyla kaydedilir ve IDE dışında kullanılabilir. Bu düzenleyici katıştırılabiliyorsanız IDE 'deki bir pencere içinde görünür. Katıştırılamaz, ayrı bir üst düzey pencere oluşturulur.

**hiyerarşi**  
Düğüm ağacı, her düğüm bir özellikler kümesiyle ilişkilidir.

**bağımsız en üst düzey bileşen**  
Kalıcı en üst düzey pencere kullanan ve tek başına uygulama penceresi olarak etkili bir şekilde çalışabilen ancak işlem içi bir nesne olarak uygulanan bir bileşen. Bu nedenle, bağımsız bir en üst düzey bileşen, IDE ile moditesi ve ileti döngüsü hizmetlerini koordine etmelidir. İşlem içi nesneler kendi ileti döngüsüne sahip değildir.

**bilgi sağlayıcısı**  
Bilgi sağlayıcı, anahtar sözcükleri arayabileceği ve bir konu başlığı listesi döndüren bir modüldür `IVsUserContextItem` . Bilgi sağlayıcısına **F1** ve arama anahtar sözcük öğeleri sağlamak için, derlenen yardım dosyanızı kaydedin (*. HxS*) sistemle birlikte. Bu dosyalardaki yardım konuları, dinamik Yardım penceresinde gösterilen konuların listesini sağlar ve bir kullanıcının **F1** tuşuna bastığı gösterilmediğini belirtir.

**yerinde bileşen**  
`IOleInPlaceComponent`IDE 'nin sahip olduğu bir belge penceresi içinde görsel olarak bulunan bir pencereyi yönetmek için arabirimini uygulayan bir VSPackage nesnesi. Yerinde bileşenler standart OLE menüsüne katılmaz-birleştirme; Bunun yerine, Kullanıcı arabirimi öğelerini IDE ile tümleştirirler.

İki tür yerinde bileşen vardır: hardkablolu yerinde bileşenler ve bileşen denetimleri.

Hardkablolu yerleşik bileşenlerinde, IDE 'nin doğrudan üzerinde oluşturulmuş gibi görünen, IDE Kullanıcı arabirimine sıkı bir şekilde tümleştirilmiş menüler, araç çubukları ve komutlar bulunur.

Bileşen denetimleri IDE ile tümleştirilmiş kendi kullanıcı arabirimi öğelerinden hiçbirini içermez; Bunun yerine IDE 'nin menülerini, komutlarını ve araç çubuklarını kullanır. Örneğin, kalın komutu, bir forma katıştırılmış olan zengin metin denetimindeki seçili bir sözcüğü kalýn olması için kullanılabilir. Ancak, bileşen denetimleri, bileşene özgü dinamik olarak yüklenen Kullanıcı arabirimi öğelerinin görüntülenmesini isteyebilir.

**Dil hizmeti**  
VSPackage geliştiricilerinin, metin işaretleme ve renklendirme gibi bilgisayar dil kodu düzenleyicilerinin özelliklerini uygulamasına izin veren bir nesne kümesi.

**Çeşitli dosyalar projesi**  
herhangi bir projede olmayan dosyaları açmak için kullanılan Project. Bu projedeki öğelerin listesi kalıcı değil.

**Proje**  
Projeler hiyerarşi nesnelerinden veya arabirimini uygulayan COM nesnelerinden oluşur `IVsHierarchy` .

**projeye özgü tasarımcı veya düzenleyici**  
Proje türünden bağımsız olarak kullanılamayan bir tasarımcı. Projeye özgü tüm tasarımcılar, kayıt defterine kendi düzenleyici fabrikası bilgilerini girmelidir. Daha sonra, belirli bir projede belirli bir dosya türü açıldığında, bu, tasarımcıyı bir kez oluşturabilir.

**Proje türü pencere**  
Genel seçim bağlamından etkin olan proje hiyerarşisini ve öğeyi sürekli olarak takip eden bir pencere. Project tür windows, değişiklikleri IDE'yi uyarıp kullanıcıya geri bildirim `SVsTrackSelectionEx` görüntülemek için hizmeti kullanır. Çözüm Gezgini bir proje türü penceresi örneğidir.

**Özellik penceresi**  
Daha önce Özellik Tarayıcısı.

**başvuru tabanlı projeler**  
Project proje dosyalarının aynı dizinde olması gerektiryen bir uygulamadır. Bunun yerine, diğer ilgisiz dizinlerden dosyalara yapılan başvurular projenin kendisi tarafından depolanır ve korunur.

**belge tablosu çalıştırma**  
IDE'nin açık olan tüm belgelerin listesinin bakımının hangi dahili yapıda olduğu. Listede, belgelerin şu anda düzende olup olmadığına bakılmaksızın bellekte açık olan tüm belgeler yer alıyor. Belge, bir düzenleyicide açılan saklı yordamlar, proje dosyaları veya ana proje dosyası (örneğin, *.vcproj dosyası) dahil olmak üzere kaydedilen herhangi bir öğedir.

**seçim bağlamı**  
IDE'de her pencerenin ayrıntılarına yer alan ve etkin seçimleri izlemek için kullanılan veriler. Seçim bağlamı şunların oluşur:

- Proje `IVsHierarchy` hiyerarşisinin arabirimine işaretçi
- Proje öğesinin öğe tanımlayıcısı.
- Etkin nesneler `ISelectionContainer` için özelliklere erişim sağlayan arabirim işaretçisi.
- Öğe değerleri dizisi.

**Hizmet**  
Tek bir COM nesnesinde bulunan com arabirimleri kümesi için sözleşme. GUID ile tanımlanan bir hizmet oluşturma, hizmeti yürüten COM arabirimleri kümesi tanımlar. COM nesneleri, birbirleriyle iletişim kurmak için hizmetleri kullanır.

**Çözüm**  
Kullanıcının birlikte çalışması ile ilgili proje grubu.

**standart tasarımcı**  
Proje türünden bağımsız olarak kullanılmaktadır. Tüm standart tasarımcıların kayıt defterine Editor Factory bilgilerini girmeleri gerekir. Daha sonra IDE, belirli bir uzantıya sahip bir dosya her açıldığında tasarımcının örneğini oluşturabilir. Verilerin bir dosyada kalıcı olması gerekir.

**standart düzenleyici**  
Herhangi bir proje türünden bağımsız olarak kullanılmaktadır düzenleyici. Bu tür düzenleyicilerde kayıt defterinde EditorFactories kayıtlıdır. Bu, IDE'nin düzenleyiciyi bulup çağırmasını sağlar.

**standart işletim sistemi düzenleyicisi**  
Belirli olmayan bir ekleme Visual Studio. İyi bilinen Win32 anahtarları kullanılarak kaydedilir (örneğin, Win32 Gezgini'nin nasıl çağrılacaklarını bilir). Böyle bir düzenleyici katıştırılanana sahipse düzenleyici, IDE'nin yerine yine de ortaya çıktı. Aksi takdirde, bu tür düzenleyiciler için ayrı bir üst düzey pencere oluşturulur.

**subcontext bag**  
Bağlam `IVsUserContext` çantasına bağlı bir nesne. nesnesi, IDE bileşeni içinde bir seçim için arama anahtar sözcüklerini, **F1** anahtar sözcüklerini ve öznitelikleri tutar. Alt metin örnekleri arasında araç penceresindeki bir komut veya düzenleyicide anahtar sözcük yer alır.

**Görev listesi**  
IDE tarafından uygulanan ve etkin görevlerin listesini görüntüleyen araç penceresi.

**metin arabelleği**  
nesnesinin ortak `VSTextBuffer` adı.

**Metin görünümü**  
nesnesinin ortak `VSTextView` adı.

**araç üst düzey bileşeni**  
IDE'nin kullanıcı arabirimiyle sıkı bir şekilde eşgüderek, modeless popup penceresi olarak çalışan bir bileşen. Bağımsız üst düzey bileşenler gibi, araç üst düzey bileşenleri de kalıcılık ve ileti döngüsü hizmetlerini IDE ile koordine etmek gerekir.

**üst düzey bileşen**  
IDE penceresinin istemci alanı yerine, modeless üst düzey bir pencereyi yöneten VSPackage nesnesi. Üst düzey bileşenler, boşta `IOleComponent` kalma süresi gibi ileti döngüsü hizmetlerinden yararlanmak için arabirimini uygulamaya alır.

**Kullanıcı arabirimi etkin**  
Görünür ve şu anda odakta olan bir VSPackage nesnesi.

**UI hiyerarşisi**  
Hiyerarşinin görüntüsüne izin `IVsUIHierarchy` vermek için arabirimi uygulayan com nesnesi. UI hiyerarşi penceresi, kullanıcı arabirimini güncelleştiren arabirimi Özellikler penceresi; diğer proje türü `ISelectionContainer` pencereleri, istenirse bu uygulama kullanabilir.

**VSCT**  
Visual Studio Tablosu'na bakın. .vsct dosyası, XML biçiminde menülerin, araç çubuklarının ve komutların yerleşimi ve davranışları hakkında bilgi içerir.

**Vspackage**  
Aşağıdaki öğelerden birini veya daha fazlasını katkıda bulundurarak IDE'nin Visual Studio genişleten, yüklenebilir bir yazılım parçası: kullanıcı arabirimi, hizmetler, proje türleri veya düzenleyici/tasarımcı. VSPackage, arabirimi uygulayan bir COM nesnesi ve seçimi ve diğer özellikleri desteklemek için diğer arabirimleri uygulayan bir veya daha fazla `IVsPackage` COM nesnesi içerir. Ayrıca VSPackage'ın belirli kayıt gereksinimleri vardır.
