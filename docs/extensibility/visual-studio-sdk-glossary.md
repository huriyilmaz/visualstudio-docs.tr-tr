---
title: Visual Studio SDK Sözlük | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 332e606e689e9394f2fcdc8cbc902e2d4a6e5ab5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698165"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK sözlüğü
Bu sözlük, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] belgelerde kullanılan terimler için tanımlar sağlar.

## <a name="terms"></a>Koşullar
 eklenti Bir yardımcı program uygulaması, sürücü veya diğer yazılım birincil bir uygulamaya eklendi. Visual Studio entegre geliştirme ortamında (IDE), eklenti IDE'nin yeteneklerini genişleten Otomasyon tabanlı bir uygulamadır.

 otomasyon modeli Visual Studio'nun önceki sürümlerinde genişletilebilirlik modeli olarak bilinen otomasyon modeli, IDE'yi yönlendiren temel yordamlara erişmenizi sağlayan bir programlama arabirimidir. Eklentiler, sihirbazlar ve makrolar, IDE'nin işlevselliğini denetlemek veya genişletmek için otomasyon modelindeki nesneleri kullanır.

 bir Guid'in UI bağlamını, araç çubuğu gibi bir UI komutunun veya öğenin görünürlüğüyle birlikte komutu. Komut UI bağlamı, bir pencereye bağlı olmadığı için seçim bağlamından farklı.

 Komut UI bağlamı için kullanılabilir:

- Belirli bir pencere etkinleştirildiğinde görünen bir araç çubuğuna GUID atayın.

- VSPackage yüklemek veya çalıştırmak zorunda kalmadan bir komutun kullanılabilirliğine GUID atayın.

- Etkin anahtar bağlamayı etkileyecek bir GUID atayın.

- Makro kaydını açmak için bir GUID atayın.

- Hata ayıklama modunu etkinleştirmek veya bir düzenleyicide tasarım ve çalıştırma modu arasında geçiş yapmak için bir GUID atayın.

  bileşen Yazılımın uygulanması hakkında önceden varolan herhangi bir bilgiye sahip olmadan bir uygulamanın işlevselliğinin bir parçası yapılabilir yazılım parçası. Bir bileşen ve uygulama arasındaki iletişim yalnızca OLE stili arabirimleri aracılığıyla yapılır.

  bileşen yöneticisi Üst `SOleComponentManager`düzey bileşenler için kullanıcı dışı arabirim koordinasyon hizmetleri sağlayan bir hizmet. Hizmet `SOleComponentManager` `IOleComponentManager` arabirimi uygular.

  bileşen UI yöneticisi `SOleComponentUIManager`Kullanıcı arabirimi koordinasyon hizmetleri sağlayan bir hizmet. Hizmet `SOleComponentUIManager` uygular `IOleComponentUIManager` ve `IOleInPlaceComponentUIManager` arayüzleri.

  bağlam çantası `IVsUserContext` Bir ortam bileşenine bağlı bir nesne (COM nesnesi). Bu nesne, arama anahtar kelimeleri, **F1** anahtar kelimeleri ve bileşenle ilgili öznitelikleri tutar. Bağlam çantaları ayrıca onlara bağlı herhangi bir alt bağlam çanta işaret.

  bağlam sağlayıcısı IDE'de onunla ilişkili bir bağlam çantası olan bir bileşen. Bu bileşenler bir araç penceresi, düzenleyici veya proje hiyerarşisi içerir.

  tasarımcı Kullanıcıların Kullanıcı Arabirimi (formlar, düğmeler ve diğer denetimler) öğelerini işlemesine olanak tanıyan bir programlama arabirimi.

  DocData A COM nesnesi belge/görünüm ayrımının olduğu bir dünyada bir belgenin temel verilerini kapsüller (örneğin, metin düzenleyicisi durumunda, bu tüm metin düzenleyicisi görünümlerinin altında yatan metin arabelleği olacaktır). EditorFactory bu nesneyi tedarik etmezse, IDE kendi adına bir nesne üretir. Bu nesnenin sorumluluğu, veri kalıcılığını ve aynı `DocData`üzerinde birden çok görünüm için paylaşım semantiklerini yönetmektir. `DocData` Nesne arabirimi `IOleCommandTarget` destekliyorsa, UIShell komut yönlendirmesi dahildir.

  DocObject Teknolojisi, konukçu tarafından sağlanan bir çerçeve içinde UI barındırmak için kullanılır. Daha ayrıntılı olarak, bu terim `IOleDocument` ve ilgili arabirimleri destekleyen herhangi bir katıştırma anlamına gelir. Bu teknoloji, COM belgelerinin uygulama ayrıntısı, Visual Basic 5.0'daki araç pencereleri, Visual Basic 6.0'daki ActiveX tasarımcıları gibi birçok potansiyel uygulamaya sahiptir.

  belge genel olarak belgeye bir bütün olarak `DocData` başvurmak `DocView`için kullanılır—hem de . Örneğin, bir DocumentFrame `DocView`bir içerir , ama aynı `DocData` zamanda kalıcılık işlemek için bir başvuru tutar.

  DocView DocObject/Embedding/WindowPane hangi kullanıcı görüntülemek ve temel işlemek `DocData`için etkileşim . Kullanıcılar arabirim tasarımının bir parçası olan Belge/Görünüm `DocObject` ayrımından yararlanamaz. Kullanıcılar, temel altında yatan verilerin daha soyut (ve daha az biçimlendirilmiş) bir kavramını `DocData`kullanmak yerine bir görünüm olarak hareket etmek için tüm Bir DocObject'i kullanır. `DocView`nesneler her zaman IDE Belge çerçeve nesneleri (MDI alt pencereler) ile katıştırılmış.

  DTE `DTE` (Geliştirme Araçları Genişletilebilirlik) nesnesi, Visual Studio otomasyon modelinde en üstteki erişim noktasıdır ve bu da IDE'yi programlı olarak otomatikleştirmenize ve genişletmenize olanak tanır.

  Dinamik Yardım penceresi IDE tarafından uygulanan ve arama anahtar sözcüğü veya **F1** Yardım konularının listesini görüntüleyen Araç penceresi.

  editör Kodu (sınıf, CLSID) `DocView`uygular. Görünüm ve `DocData` veri ayrımı desteklenirse de uygular.

  uzantısı Bir IDE'yi değiştiren, özelleştiren veya ekleyen bir özellik. Otomasyon modelini veya VSPackages'i kullanarak uzantılar oluşturursunuz.

  dış düzenleyici Microsoft Word gibi IDE'ye özgü olmayan bir düzenleyici. Kendi mekanizmaları ile kaydedilmiştir ve IDE dışında kullanılabilir. Bu düzenleyici katıştırılmış olabilirse, IDE'deki bir pencerenin içinde görünür. Katıştırılamazsa, ayrı bir üst düzey pencere oluşturulur.

  hiyerarşi Düğümler Ağacı, her düğüm özellikleri kümesi ile ilişkili.

  bağımsız üst düzey bileşen Modeless üst düzey pencere kullanan ve tek başına bir uygulama penceresi olarak etkin bir şekilde çalışabilen, ancak işlem içi nesne olarak uygulanan bileşen. Bu nedenle, bağımsız bir üst düzey bileşen, yöntem ve ileti döngüsü hizmetlerini IDE ile koordine etmelidir. İşlem içi nesnelerin kendi ileti döngüleri yoktur.

  bilgi sağlayıcısı Bilgi sağlayıcısı, anahtar kelimeleri arayabilen ve `IVsUserContextItem` nesnelerin biçiminde bir konu listesini döndürebilen bir modüldür. Bilgi sağlayıcısı için **F1** ve arama anahtar kelime öğeleri sağlamak için, derlenmiş Yardım dosyanızı kaydedin (*. HxS*) sistemi ile. Bu dosyalardaki Yardım konuları Dinamik Yardım penceresinde görüntülenen konuların listesini sağlar ve kullanıcının **F1**tuşuna basıp basmadığını gösterir.

  yerinde bileşen IDE'ye `IOleInPlaceComponent` ait bir belge penceresinde görsel olarak bulunan bir pencereyi yönetmek için arabirimi uygulayan a VSPackage nesnesi. Yerinde bileşenler standart OLE menü birleştirme çalışmalarına katılmaz; bunun yerine kullanıcı arabirim öğelerini IDE'ye entegre ederler.

  İki tür yerinde bileşen vardır: yerinde sabit bileşenler ve bileşen denetimleri.

  Kablolu yerinde bileşenler, IDE'nin kullanıcı arabirimine sıkıca entegre edilmiş menülere, araç çubuklarına ve komutlara sahiptir ve bunlar doğrudan IDE'ye entegre edilmiş gibi görünür.

  Bileşen denetimlerinde IDE'ye entegre edilmiş kendi kullanıcı arabirimi öğeleri yoktur; bunun yerine IDE menülerini, komutlarını ve araç çubuklarını kullanırlar. Örneğin, Kalın komutu, bir forma katıştırılmış zengin bir metin denetimi içinde seçili bir sözcüğü kalınyapmak için kullanılabilir. Ancak, bileşen denetimleri dinamik olarak yüklenen bileşene özgü UI öğelerinin görüntülenmesini isteyebilir.

  dil hizmeti VSPackage geliştiricilerinin metin işaretleme ve renklendirme gibi bilgisayar dili kodu düzenleyicilerinin özelliklerini uygulamasına olanak tanıyan nesneler kümesi.

  Çeşitli Dosyalar proje Projesi, herhangi bir projede olmayan açık dosyaları barındırmak için kullanılır. Bu projedeki öğelerin listesi kalıcı değil.

  proje Projeleri hiyerarşi nesnelerinden veya `IVsHierarchy` arabirimi uygulayan COM nesnelerinden oluşur.

  projeye özel tasarımcı veya düzenleyici Proje türünden bağımsız olarak kullanılabilen bir tasarımcı. Projeye özel tüm tasarımcılar, Editör Fabrikası bilgilerini kayıt defterine girmelidir. IDE, belirli bir projede belirli bir dosya türü açıldığında tasarımcıyı anında anlayabilir.

  proje türü penceresi Genel seçim bağlamından sürekli olarak etkin olan proje hiyerarşisini ve öğeyi izleyen bir pencere. Proje tipi `SVsTrackSelectionEx` pencereler, IDE'yi değişiklikler konusunda uyarmak ve kullanıcıya geri bildirim görüntülemek için hizmeti kullanır. Çözüm Gezgini, proje türü penceresine bir örnektir.

  Özellikler penceresi Eski Özellik Tarayıcı.

  başvuru tabanlı projeler Projenin aynı dizinde olması için dosyaların gerektirmeyen projesi. Bunun yerine, diğer ilgisiz dizinlerden gelen dosyalara yapılan başvurular projenin kendisi tarafından depolanır ve korunur.

  çalışan belge tablosu IDE'nin şu anda açık olan tüm belgelerin listesini oluşturduğu iç yapı. Liste, belgelerin şu anda düzenlenip düzenlenmediğine bakılmaksızın bellekteki tüm açık belgeleri içerir. Belge, düzenleyicide açılan saklı yordamlar, projedeki dosyalar veya ana proje dosyası (örneğin, *.vcproj dosyası) dahil olmak üzere kaydedilen herhangi bir öğedir.

  seçim bağlamı IDE'deki her pencerenin ayrıntısının bir parçası olan ve etkin seçimleri izlemek için kullanılan veriler. Seçim bağlamı aşağıdakilerden oluşur:

- Proje hiyerarşisinin `IVsHierarchy` arabirimine işaretçi

- Proje öğesinin madde tanımlayıcısı.

- Etkin nesnelerin `ISelectionContainer` özelliklerine erişim sağlayan arabirime işaretçi.

- Öğe değerleri dizisi.

  hizmet Tek bir COM nesnesinde bulunan bir COM arabirimi kümesi için bir sözleşme. GUID tarafından tanımlanan bir hizmet oluşturduğunuzda, hizmeti yürüten COM arabirimleri kümesini tanımlarsınız. COM nesneleri birbirleriyle iletişim kurmak için hizmetleri kullanır.

  bir kullanıcının birlikte çalıştığı ilgili projeler grubu.

  standart tasarımcı Proje türünden bağımsız olarak kullanılabilecek bir tasarımcı. Tüm standart tasarımcılar, Editör Fabrikası bilgilerini kayıt defterine girmelidir. IDE daha sonra belirli bir uzantılı bir dosya açıldığında tasarımcıyı anında anlayabilir. Veriler bir dosyada devam etmelidir.

  belirli bir proje türünden bağımsız olarak kullanılabilecek standart düzenleyici düzenleyici. Bu tür editörlerin kayıt defterine kayıtlı EditorFactorys vardır. Bu, IDE'nin düzenleyiciyi bulmasını ve çağırmasını sağlar.

  standart işletim sistemi editörü Visual Studio'ya özgü olmayan bir katıştırma. Tanınmış Win32 tuşları kullanılarak kaydedilir (örneğin, Win32 Explorer nasıl çağırılabildiğini bilir). Böyle bir düzenleyici katıştırılmış olabilir, editör hala IDE onun yerine gösterir. Aksi takdirde, bu tür editörler için ayrı bir üst düzey pencere oluşturulur.

  alt bağlam `IVsUserContext` çantası Bağlam çantasına bağlı bir nesne. Nesne, bir IDE bileşeni içindeki bir seçim için arama anahtar kelimeleri, **F1** anahtar kelimeleri ve öznitelikleri tutar. Alt bağlam örnekleri, araç penceresindeki bir komutveya düzenleyicideki bir anahtar kelimedir.

  Görev listesi IDE tarafından uygulanan ve etkin görevlerin listesini görüntüleyen araç penceresi.

  metin arabelleği Nesne `VSTextBuffer`için ortak ad .

  Metin görünümü Nesne `VSTextView`için ortak ad .

  araç üst düzey bileşen IDE kullanıcı arabirimi ile sıkıca koordine, modsuz bir pop-up penceresi olarak çalışan bir bileşen. Bağımsız üst düzey bileşenler gibi, takım üst düzey bileşenleri de IDE ile yöntem ve ileti döngüsü hizmetlerini koordine etmelidir.

  üst düzey bileşen IDE penceresinin istemci alanı yerine modsuz üst düzey bir pencereyi yöneten bir VSPackage nesnesi. Üst düzey bileşenler, `IOleComponent` boşta kalma süresine erişim gibi ileti döngüsü hizmetlerinden yararlanmak için arabirimi uygular.

  UI etkin A VSPackage nesnesi görünür ve şu anda odak vardır.

  UI hiyerarşisi Bir hiyerarşinin `IVsUIHierarchy` görüntülenmesine izin vermek için arabirimi uygulayan bir COM nesnesi. UI hiyerarşisi penceresi `ISelectionContainer` Özellikleri penceresini güncelleştirmek için arabirimi uygular; diğer proje türü pencereler, istenirse bu uygulamayı kullanabilirsiniz.

  VSCT Visual Studio Komut Tablosu. .vsct dosyası, XML formatında menülerin, araç çubuklarının ve komutların yerleşimi ve davranışları hakkında bilgi içerir.

  VSPackage Aşağıdaki öğelerden birini veya birkaçını katkıda bulunarak Visual Studio IDE'yi genişleten yüklenebilir bir yazılım dır: kullanıcı arabirimi, hizmetler, proje türleri veya düzenleyici/tasarımcı. VSPackage, `IVsPackage` arabirimi ve seçimi ve diğer özellikleri desteklemek için diğer arabirimleri uygulayan bir veya daha fazla diğer COM nesnesini uygulayan bir COM nesnesi oluşur. Buna ek olarak, bir VSPackage belirli kayıt gereksinimleri vardır.
