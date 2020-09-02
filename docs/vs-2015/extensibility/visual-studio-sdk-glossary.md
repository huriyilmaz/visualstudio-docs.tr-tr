---
title: Visual Studio SDK sözlüğü | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c189c4c9e06d224d7cef296a2c39e732cbc29f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538721"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK Sözlüğü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sözlük, belgelerde kullanılan terimlere yönelik tanımlar sağlar [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
## <a name="terms"></a>Terimler  
 eklenti  
 Bir yardımcı program uygulaması, sürücü veya bir birincil uygulamaya eklenen diğer yazılımlar. Visual Studio tümleşik geliştirme ortamında (IDE), eklenti IDE 'nin yeteneklerini genişleten Otomasyon tabanlı bir uygulamadır.  
  
 otomatikleştirme modeli  
 Visual Studio 'nun önceki sürümlerinde genişletilebilirlik modeli olarak bilinen otomasyon modeli, IDE 'yi hedefleyen temel yordamlara erişmenizi sağlayan bir programlama arabirimidir. Eklentiler, sihirbazlar ve makrolar, IDE 'nin işlevselliğini denetlemek veya genişletmek için Otomasyon modelindeki nesneleri kullanır.  
  
 komut UI bağlamı  
 Bir GUID 'in, bir kullanıcı arabirimi komutunun veya bir araç çubuğu gibi bir öğenin görünürlüğiyle ilişkilendirilmesi. Komut UI bağlamı, bir pencereye eklenmemiş seçim bağlamından farklı.  
  
 Komut UI bağlamı şu şekilde kullanılabilir:  
  
- Belirli bir pencere etkinleştirildiğinde görüntülenen bir araç çubuğuna GUID atayın.  
  
- Bir VSPackage yüklemesine veya çalıştırmaya gerek kalmadan bir komutun kullanılabilirliğine bir GUID atayın.  
  
- Etkin anahtar bağlamasını etkilemek için bir GUID atayın.  
  
- Makro kaydını açmak için bir GUID atayın.  
  
- Hata ayıklama modunu etkinleştirmek veya bir düzenleyicide tasarım ve çalıştırma modu arasında geçiş yapmak için bir GUID atayın.  
  
  bileşenleri  
  Uygulamanın, yazılımın uygulamasıyla ilgili önceden mevcut herhangi bir bilgi sahibi olmadan, uygulamanın işlevselliğinin bir parçası haline getirilebilir yazılım parçası. Bir bileşen ile uygulama arasındaki iletişim yalnızca OLE stil arabirimleri aracılığıyla yapılır.  
  
  Bileşen Yöneticisi  
  `SOleComponentManager`En üst düzey bileşenlere yönelik kullanıcı arabirimi koordinasyon hizmetleri sağlayan bir hizmet. `SOleComponentManager`Hizmet, arabirimini uygular `IOleComponentManager` .  
  
  bileşen Kullanıcı Arabirimi Yöneticisi  
  `SOleComponentUIManager`Kullanıcı arabirimi koordinasyon hizmetleri sağlayan bir hizmet. `SOleComponentUIManager`Hizmet, `IOleComponentUIManager` ve arabirimlerini uygular `IOleInPlaceComponentUIManager` .  
  
  bağlam paketi  
  `IVsUserContext`Ortam bileşenine eklenmiş bir nesne (com nesnesi). Bu nesne, bileşenle ilgili arama anahtar sözcüklerini, F1 anahtar sözcüklerini ve öznitelikleri barındırır. Bağlam paketleri buna bağlı olan herhangi bir alt bağlam torbaya işaret edilir.  
  
  bağlam sağlayıcısı  
  IDE içinde kendisiyle ilişkili bir bağlam paketi olan bir bileşen. Bu tür bileşenler bir araç penceresi, düzenleyici veya proje hiyerarşisi içerir.  
  
  tasarımcı  
  Kullanıcıların UI (formlar, düğmeler ve diğer denetimler) öğelerini işlemesini sağlayan bir programlama arabirimi.  
  
  DocData  
  Belge/görünüm ayrımı (örneğin, metin düzenleyici durumunda, bu, tüm metin Düzenleyicisi görünümlerini temel alan metin arabelleği) olan bir dünyanın temel verilerini kapsayan bir COM nesnesi. EditorFactory bu nesneyi sağlamadıysanız, IDE onun adına bir tane üretecektir. Bu nesnenin sorumluluğu, aynı şekilde birden fazla görünüm için veri kalıcılığını ve paylaşım semantiğini yönettiğdedir `DocData` . `DocData`Nesne `IOleCommandTarget` arabirimini destekliyorsa, UIShell komut yönlendirmesine dahil edilir.  
  
  DocObject  
  Kullanıcı arabirimini konak tarafından sunulan bir çerçeve içinde barındırmak için kullanılan teknoloji. Daha belirgin olarak, bu terim ve ilgili arabirimleri destekleyen herhangi bir eklemeye başvurur `IOleDocument` . Bu teknolojide COM belgelerinin uygulama ayrıntısı, Visual Basic 5,0 ' deki araç pencereleri, Visual Basic 6,0 ' deki ActiveX tasarımcıları vb. gibi birçok olası uygulama vardır.  
  
  belge  
  Bir bütün olarak belgeye genel olarak başvurmak için kullanılır — `DocData` ve `DocView` . Örneğin, bir Belgebir çerçeve bir içerir `DocView` , ancak kalıcılığı işlemek için öğesine bir başvurusu da saklar `DocData` .  
  
  DocView  
  Kullanıcının temel olarak görüntülemek ve işlemek için etkileşimde bulunduğu DocObject/katıştırma/WindowPane `DocData` . Kullanıcıların, arabirim tasarımının parçası olan belge/görünüm ayrımı özelliğinden yararlanmadığını unutmayın `DocObject` . Kullanıcılar, olarak bilinen temel alınan verilerin daha soyut (ve daha az şekillendirilmiş) bir kavramı kullanmak yerine bir görünüm görevi gören bir tüm DocObject kullanır `DocData` . `DocView` nesneler, IDE 'nin belge çerçevesi nesneleriyle (MDI alt pencereleri) her zaman katıştırılır.  
  
  MIÞTIR  
  `DTE`(Geliştirme araçları genişletilebilirliği) nesnesi, Visual Studio Automation modelindeki en üst erişim noktasıdır ve IDE 'yi programlı bir şekilde otomatikleştirmenize ve genişletmenize olanak tanır.  
  
  Dinamik Yardım penceresi  
  IDE tarafından uygulanan ve arama anahtar sözcüğü veya F1 Yardım konuları listesini görüntüleyen araç penceresi.  
  
  düzenleyici  
  Öğesini uygulayan kod (sınıf, CLSID) `DocView` . Ayrıca `DocData` Görünüm/veri ayrımı destekleniyorsa de uygular.  
  
  uzantı  
  IDE 'ye değiştiren, özelleştiren veya ekleyen bir özellik. Otomasyon modeli veya VSPackages kullanarak uzantılar oluşturursunuz.  
  
  Dış düzenleyici  
  IDE 'ye özgü olmayan, Microsoft Word gibi bir düzenleyici. Kendi mekanizmaları aracılığıyla kaydedilir ve IDE dışında kullanılabilir. Bu düzenleyici katıştırılabiliyorsanız IDE 'deki bir pencere içinde görünür. Katıştırılamaz, ayrı bir üst düzey pencere oluşturulur.  
  
  hiyerarşi  
  Düğüm ağacı, her düğüm bir özellikler kümesiyle ilişkilidir.  
  
  bağımsız en üst düzey bileşen  
  Kalıcı en üst düzey pencere kullanan ve tek başına uygulama penceresi olarak etkili bir şekilde çalışabilen ancak işlem içi bir nesne olarak uygulanan bir bileşen. Bu nedenle, bağımsız bir en üst düzey bileşen, IDE ile moditesi ve ileti döngüsü hizmetlerini koordine etmelidir. İşlem içi nesneler kendi ileti döngüsüne sahip değildir.  
  
  bilgi sağlayıcısı  
  Bilgi sağlayıcısı, anahtar kelimeleri arayabileceği ve bir konu listesini nesneler biçiminde döndüresağlayan bir modüldür `IVsUserContextItem` . Bilgi sağlayıcısına F1 ve arama anahtar sözcük öğeleri sağlamak için, derlenen yardım dosyanızı kaydedin (. HxS) sistemle birlikte. Bu dosyalardaki yardım konuları, dinamik Yardım penceresinde görüntülenen konuların listesini sağlamak için kullanılır ve bir kullanıcının F1 tuşuna bastığı gösterilmediğini belirtir.  
  
  yerinde bileşen  
  `IOleInPlaceComponent`IDE 'nin sahip olduğu bir belge penceresi içinde görsel olarak bulunan bir pencereyi yönetmek için arabirimini uygulayan bir VSPackage nesnesi. Yerinde bileşenler standart OLE menüsü-birleştirme 'a katılmaz; Bunun yerine, Kullanıcı arabirimi öğelerini IDE ile tümleştirirler.  
  
  İki tür yerinde bileşen vardır: hardkablolu yerinde bileşenler ve bileşen denetimleri.  
  
  Hardkablolu yerleşik bileşenlerinde, IDE 'nin doğrudan üzerinde oluşturulmuş gibi görünen, IDE Kullanıcı arabirimine sıkı bir şekilde tümleştirilmiş menüler, araç çubukları ve komutlar bulunur.  
  
  Bileşen denetimleri IDE ile tümleştirilmiş kendi kullanıcı arabirimi öğelerinden hiçbirini içermez; Bunun yerine IDE 'nin menülerini, komutlarını ve araç çubuklarını kullanır. Örneğin, kalın komutu, bir forma katıştırılmış olan zengin metin denetimindeki seçili bir sözcüğü kalýn olması için kullanılabilir. Ancak, bileşen denetimleri, bileşene özgü dinamik olarak yüklenen Kullanıcı arabirimi öğelerinin görüntülenmesini isteyebilir.  
  
  Dil hizmeti  
  VSPackage geliştiricilerinin, metin işaretleme ve renklendirme gibi bilgisayar dil kodu düzenleyicilerinin özelliklerini uygulamasına izin veren bir nesne kümesi.  
  
  Çeşitli dosyalar projesi  
  Proje, herhangi bir projede yer alan dosyaları açmak için kullanılır. Bu projedeki öğelerin listesi kalıcı değil.  
  
  proje  
  Projeler hiyerarşi nesnelerinden veya arabirimini uygulayan COM nesnelerinden oluşur `IVsHierarchy` .  
  
  projeye özgü tasarımcı veya düzenleyici  
  Proje türünden bağımsız olarak kullanılamayan bir tasarımcı. Projeye özgü tüm tasarımcılar, kayıt defterine kendi düzenleyici fabrikası bilgilerini girmelidir. Daha sonra, belirli bir projede belirli bir dosya türü açıldığında, bu, tasarımcıyı bir kez oluşturabilir.  
  
  Proje türü pencere  
  Şu anda etkin olan proje hiyerarşisini ve öğeyi genel seçim bağlamından izleyen bir pencere. Proje türü Windows, `SVsTrackSelectionEx` DEĞIŞIKLIKLERI IDE 'ye uyarı vermek ve kullanıcıya geri bildirim göstermek için hizmeti kullanın. Çözüm Gezgini bir proje türü pencere örneğidir.  
  
  Özellik penceresi  
  Eski adıyla özellik tarayıcısı.  
  
  başvuru tabanlı projeler  
  Projenin dosyaları gerektirmeyen proje aynı dizinde olmalıdır. Bunun yerine, diğer ilişkisiz dizinlerden dosyalara yapılan başvurular proje tarafından saklanır ve saklanır.  
  
  çalıştırılan belge tablosu  
  IDE 'nin şu anda açık olan tüm belgelerin listesini koruduğu iç yapı. Bu liste, belgelerin Şu anda düzenlenip düzenlenmediğine bakılmaksızın bellekteki tüm açık belgeleri içerir. Belge, bir düzenleyicide açılan saklı yordamlar, projedeki dosyalar veya ana proje dosyası (örneğin, *. vcproj dosyası) dahil olmak üzere, kaydedilen herhangi bir öğedir.  
  
  seçim bağlamı  
  IDE 'deki her pencerenin ayrıntılarının parçası olan ve etkin seçimleri izlemek için kullanılan veriler. Seçim bağlamı aşağıdakilerden oluşur:  
  
- `IVsHierarchy`Proje hiyerarşisinin arabirimine yönelik işaretçi  
  
- Proje öğesinin öğe tanımlayıcısı.  
  
- `ISelectionContainer`Etkin nesneler için özelliklere erişim sağlayan arabirime yönelik işaretçi.  
  
- Öğe değerleri dizisi.  
  
  hizmet  
  Tek bir COM nesnesinde bulunan bir COM arabirimleri kümesi için bir anlaşma. Bir GUID tarafından tanımlanan bir hizmet oluşturduğunuzda, hizmeti yürüten COM arabirimleri kümesini tanımlarsınız. COM nesneleri bir birbirleriyle iletişim kurmak için Hizmetleri kullanır.  
  
  çözümden  
  Kullanıcının çalıştığı ilgili projeler grubu.  
  
  Standart tasarımcı  
  Proje türünden bağımsız olarak kullanılabilecek bir tasarımcı. Tüm standart tasarımcılarının kayıt defterine kendi Düzenleyici Fabrika bilgilerini girmesi gerekir. Daha sonra, belirli bir uzantıya sahip bir dosya açıldığında IDE, tasarımcı örneğini oluşturabilir. Verilerin bir dosyada kalıcı olması gerekir.  
  
  Standart düzenleyici  
  Belirli bir proje türünden bağımsız olarak kullanılabilecek düzenleyici. Bu tür düzenleyicilerde kayıt defterine kayıtlı EditorFactory vardır. Bu, IDE 'nin düzenleyiciyi bulmasını ve çağırabilmesini sağlar.  
  
  standart işletim sistemi Düzenleyicisi  
  Visual Studio 'Ya özgü olmayan bir katıştırma. Bu, iyi bilinen Win32 anahtarları kullanılarak kaydedilir (örneğin, Win32 Explorer nasıl çağıracağını bilir). Böyle bir düzenleyici gömülebilir, düzenleyici, IDE 'deki yerinde görünür. Aksi takdirde, bu tür düzenleyiciler için ayrı bir üst düzey pencere oluşturulur.  
  
  alt bağlam paketi  
  `IVsUserContext`Bağlam çantasına bağlı bir nesne. Bu nesne, IDE bileşeni içindeki bir seçimin arama anahtar sözcüklerini, F1 anahtar sözcüklerini ve özniteliklerini barındırır. Alt bağlam örnekleri araç penceresinde bir komut veya bir düzenleyicide anahtar sözcük içerir.  
  
  Görev listesi  
  IDE tarafından uygulanan ve etkin görevlerin bir listesini görüntüleyen araç penceresi.  
  
  metin arabelleği  
  Nesnenin ortak adı `VSTextBuffer` .  
  
  Metin görünümü  
  Nesnenin ortak adı `VSTextView` .  
  
  Araç üst düzey bileşeni  
  Kalıcı açılan pencere olarak çalışan ve IDE 'nin Kullanıcı arabirimiyle sıkı şekilde çalışan bir bileşen. Bağımsız en üst düzey bileşenler gibi, araç üst düzey bileşenleri de IDE ile de modlık ve ileti döngüsü hizmetlerini koordine etmelidir.  
  
  üst düzey bileşen  
  IDE penceresinin istemci alanı yerine geçici bir üst düzey pencereyi yöneten VSPackage nesnesi. En üst düzey bileşenler, `IOleComponent` boşta kalma süresine erişim gibi ileti döngüsü hizmetlerinden faydalanmak için arabirimi uygular.  
  
  UI etkin  
  Görünür ve şu anda odağa sahip bir VSPackage nesnesi.  
  
  UI hiyerarşisi  
  `IVsUIHierarchy`Hiyerarşinin görüntülenmesini sağlamak için arabirimini uygulayan BIR com nesnesi. UI hiyerarşisi penceresi `ISelectionContainer` Özellikler penceresi güncelleştirmek için arabirimi uygular; isterseniz diğer proje türü pencereler bu uygulamayı kullanabilir.  
  
  VSCT  
  Visual Studio komut tablosu. . Vsct dosyası, XML biçimindeki menülerin, araç çubuklarının ve komutların yerleşimi ve davranışları hakkında bilgiler içerir.  
  
  VSPackage  
  Aşağıdakilerden birini veya daha fazlasını sunarak Visual Studio IDE 'yi genişleten, yüklenebilir bir yazılım parçasıdır: Kullanıcı arabirimi, hizmetler, proje türleri veya düzenleyici/tasarımcı. VSPackage, arabirimi uygulayan bir COM nesnesinden `IVsPackage` ve seçimi ve diğer özellikleri desteklemek için diğer arabirimleri uygulayan bir veya daha fazla com nesnesi içerir. Ayrıca, VSPackage, belirli kayıt gereksinimlerine sahiptir.
