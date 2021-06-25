---
title: Visual Studio SDK sözlüğü | Microsoft Docs
description: Bu sözlük, Visual Studio SDK belgelerinde kullanılan terimler için tanımlar sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 49e91a64220882eea196819a1860052dc871bec4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905429"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK sözlüğü
Bu sözlük, belgelerde kullanılan terimlere yönelik tanımlar sağlar [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] .

## <a name="terms"></a>Terimler
 Bir yardımcı program uygulaması, sürücü veya bir birincil uygulamaya eklenen diğer yazılımlar. Visual Studio tümleşik geliştirme ortamında (IDE), eklenti IDE 'nin yeteneklerini genişleten Otomasyon tabanlı bir uygulamadır.

 Otomasyon modeli Visual Studio 'nun önceki sürümlerinde genişletilebilirlik modeli olarak bilinen otomasyon modeli, IDE 'yi hedefleyen temeldeki yordamlara erişmenizi sağlayan bir programlama arabirimidir. Eklentiler, sihirbazlar ve makrolar, IDE 'nin işlevselliğini denetlemek veya genişletmek için Otomasyon modelindeki nesneleri kullanır.

 bir GUID 'in kullanıcı ARABIRIMI bağlam Ilişkilendirmesi bir kullanıcı arabirimi komutunun veya bir araç çubuğu gibi öğesinin görünürlüğiyle Ilişkilendirilmesi. Komut UI bağlamı, bir pencereye eklenmemiş olan seçim bağlamından farklı.

 Komut UI bağlamı şu şekilde kullanılabilir:

- Belirli bir pencere etkinleştirildiğinde görüntülenen bir araç çubuğuna GUID atayın.

- Bir VSPackage yüklemesine veya çalıştırmaya gerek kalmadan bir komutun kullanılabilirliğine bir GUID atayın.

- Etkin anahtar bağlamasını etkilemek için bir GUID atayın.

- Makro kaydını açmak için bir GUID atayın.

- Hata ayıklama modunu etkinleştirmek veya bir düzenleyicide tasarım ve çalıştırma modu arasında geçiş yapmak için bir GUID atayın.

  uygulamanın, yazılımın uygulamasıyla ilgili önceden mevcut herhangi bir bilgi sahibi olmadan, uygulamanın işlevselliğinin bir parçası haline getirilebilir bir yazılım bileşeni. Bir bileşen ile uygulama arasındaki iletişim yalnızca OLE stil arabirimleri aracılığıyla yapılır.

  Bileşen Yöneticisi `SOleComponentManager` , en üst düzey bileşenlere yönelik kullanıcı arabirimi koordinasyon hizmetleri sağlayan bir hizmet. `SOleComponentManager`Hizmet, arabirimini uygular `IOleComponentManager` .

  bileşen UI Yöneticisi `SOleComponentUIManager` , Kullanıcı arabirimi koordinasyon hizmetleri sağlayan bir hizmet. `SOleComponentUIManager`Hizmet, `IOleComponentUIManager` ve arabirimlerini uygular `IOleInPlaceComponentUIManager` .

  `IVsUserContext`ortam bileşenine eklenen bir nesne (com nesnesi) bağlam torbası. Bu nesne, bileşenle ilgili arama anahtar sözcüklerini, **F1** anahtar sözcüklerini ve öznitelikleri barındırır. Bağlam paketleri buna bağlı olan herhangi bir alt bağlam torbaya işaret edilir.

  bağlam sağlayıcısı ile ilişkili bir bağlam paketi olan IDE 'deki bir bileşen. Bu tür bileşenler bir araç penceresi, düzenleyici veya proje hiyerarşisi içerir.

  Kullanıcıların UI (formlar, düğmeler ve diğer denetimler) öğelerini işlemesini sağlayan bir programlama arabirimi tasarlayıcısı.

  DocData, belge/görünüm ayrımı olan bir dünyanın içindeki bir belgenin temel aldığı verileri kapsülleyerek bir COM nesnesi (örneğin, metin düzenleyici örneğinde, bu, tüm metin Düzenleyicisi görünümlerini temel alan metin arabelleği olacaktır). EditorFactory bu nesneyi sağlayamazsa, IDE onun adına bir tane oluşturmaz. Bu nesnenin sorumluluğu, aynı şekilde birden fazla görünüm için veri kalıcılığını ve paylaşım semantiğini yönettiğdedir `DocData` . `DocData`Nesne `IOleCommandTarget` arabirimini destekliyorsa, UIShell komut yönlendirmesine dahil edilir.

  Konak tarafından sunulan bir çerçeve içinde Kullanıcı arabirimini barındırmak için kullanılan DocObject teknolojisi. Daha belirgin olarak, bu terim ve ilgili arabirimleri destekleyen herhangi bir eklemeye başvurur `IOleDocument` . Bu teknolojide COM belgelerinin uygulama ayrıntısı, Visual Basic 5,0 ' deki araç pencereleri, Visual Basic 6,0 ' deki ActiveX tasarımcıları vb. gibi birçok olası uygulama vardır.

  bir bütün olarak belgeye genel olarak başvurmak için kullanılan belge ( `DocData` ve) `DocView` . Örneğin, bir Belgebir çerçeve bir içerir `DocView` , ancak kalıcılığı işlemek için öğesine bir başvurusu da saklar `DocData` .

  DocView kullanıcının temel aldığı görüntüleme ve düzenleme için etkileşimde bulunduğu DocObject/katıştırma/WindowPane `DocData` . Kullanıcılar, arabirim tasarımının parçası olan belge/görünüm ayrımı özelliğinden faydalanır `DocObject` . Kullanıcılar, olarak bilinen temel alınan verilerin daha soyut (ve daha az şekillendirilmiş) bir kavramı kullanmak yerine bir görünüm görevi gören bir tüm DocObject kullanır `DocData` . `DocView` nesneler, IDE 'nin belge çerçevesi nesneleriyle (MDI alt pencereleri) her zaman katıştırılır.

  DTE `DTE` (geliştirme araçları genişletilebilirliği) nesnesi, Visual Studio Automation modelindeki en üst erişim noktasıdır ve IDE 'yi programlı bir şekilde otomatikleştirmenize ve genişletmenize olanak tanır.

  IDE tarafından uygulanan ve arama anahtar sözcüğü veya **F1** yardım konuları listesini görüntüleyen dinamik Yardım penceresi araç penceresi.

  uygulayan düzenleyici kodu (sınıf, CLSID) `DocView` . Ayrıca `DocData` Görünüm ve veri ayrımı destekleniyorsa de uygular.

  IDE 'ye değiştiren, özelleştiren veya ekleyen bir özellik uzantısı. Otomasyon modeli veya VSPackages kullanarak uzantılar oluşturursunuz.

  Dış düzenleyici Microsoft Word gibi IDE 'ye özgü olmayan bir düzenleyici. Kendi mekanizmaları aracılığıyla kaydedilir ve IDE dışında kullanılabilir. Bu düzenleyici katıştırılabiliyorsanız IDE 'deki bir pencere içinde görünür. Katıştırılamaz, ayrı bir üst düzey pencere oluşturulur.

  düğümlerin hiyerarşi ağacı, her düğüm bir özellikler kümesiyle ilişkili.

  bağımsız en üst düzey bileşene, kalıcı bir en üst düzey pencere kullanan ve tek başına uygulama penceresi olarak etkili bir şekilde çalışabilen ancak işlem içi bir nesne olarak uygulanan bir bileşen. Bu nedenle, bağımsız bir en üst düzey bileşen, IDE ile moditesi ve ileti döngüsü hizmetlerini koordine etmelidir. İşlem içi nesneler kendi ileti döngüsüne sahip değildir.

  bilgi sağlayıcısı bilgi sağlayıcısı, anahtar sözcükleri arayabileceği ve bir konu başlığı listesi döndüren bir modüldür `IVsUserContextItem` . Bilgi sağlayıcısına **F1** ve arama anahtar sözcük öğeleri sağlamak için, derlenen yardım dosyanızı kaydedin (*. HxS*) sistemle birlikte. Bu dosyalardaki yardım konuları, dinamik Yardım penceresinde gösterilen konuların listesini sağlar ve bir kullanıcının **F1** tuşuna bastığı gösterilmediğini belirtir.

  yerinde bileşen, `IOleInPlaceComponent` IDE 'nin sahip olduğu bir belge penceresi içinde görsel olarak bulunan bir pencereyi yönetmek için arabirimini uygulayan bir VSPackage nesnesi. Yerinde bileşenler standart OLE menüsüne katılmaz-birleştirme; Bunun yerine, Kullanıcı arabirimi öğelerini IDE ile tümleştirirler.

  İki tür yerinde bileşen vardır: hardkablolu yerinde bileşenler ve bileşen denetimleri.

  Hardkablolu yerleşik bileşenlerinde, IDE 'nin doğrudan üzerinde oluşturulmuş gibi görünen, IDE Kullanıcı arabirimine sıkı bir şekilde tümleştirilmiş menüler, araç çubukları ve komutlar bulunur.

  Bileşen denetimleri IDE ile tümleştirilmiş kendi kullanıcı arabirimi öğelerinden hiçbirini içermez; Bunun yerine IDE 'nin menülerini, komutlarını ve araç çubuklarını kullanır. Örneğin, kalın komutu, bir forma katıştırılmış olan zengin metin denetimindeki seçili bir sözcüğü kalýn olması için kullanılabilir. Ancak, bileşen denetimleri, bileşene özgü dinamik olarak yüklenen Kullanıcı arabirimi öğelerinin görüntülenmesini isteyebilir.

  Dil hizmeti VSPackage geliştiricilerinin metin işaretleme ve renklendirme gibi bilgisayar dil kodu düzenleyicilerinin özelliklerini uygulamasına izin veren bir nesne kümesi.

  Çeşitli dosyalar proje projesi, herhangi bir projede olmayan dosyaları açmak için kullanılır. Bu projedeki öğelerin listesi kalıcı değil.

  Proje projeleri, hiyerarşi nesnelerinden veya arabirimini uygulayan COM nesnelerinden oluşur `IVsHierarchy` .

  projeye özgü tasarımcı veya düzenleyici proje türünden bağımsız olarak kullanılamayan bir tasarımcı. Projeye özgü tüm tasarımcılar, kayıt defterine kendi düzenleyici fabrikası bilgilerini girmelidir. Daha sonra, belirli bir projede belirli bir dosya türü açıldığında, bu, tasarımcıyı bir kez oluşturabilir.

  Proje türü pencere, geçerli etkin proje hiyerarşisini ve öğeyi genel seçim bağlamından sürekli izleyen bir pencere. Proje türü Windows, `SVsTrackSelectionEx` DEĞIŞIKLIKLERI IDE 'ye uyarı vermek ve kullanıcıya geri bildirim göstermek için hizmeti kullanın. Çözüm Gezgini bir proje türü pencere örneğidir.

  Daha önce Özellikler penceresi özellik tarayıcısı.

  Projenin dosyaları aynı dizinde olması gerekmeyen başvuru tabanlı proje projesi. Bunun yerine, diğer ilişkisiz dizinlerden dosyalara yapılan başvurular proje tarafından saklanır ve saklanır.

  IDE 'nin şu anda açık olan tüm belgelerin listesini tuttuğu belge tablosu Iç yapısı çalıştırılıyor. Liste, belgelerin Şu anda düzenlenip düzenlenmediğine bakılmaksızın bellekteki tüm açık belgeleri içerir. Belge, bir düzenleyicide açılan saklı yordamlar, projedeki dosyalar veya ana proje dosyası (örneğin, *. vcproj dosyası) dahil olmak üzere, kaydedilen herhangi bir öğedir.

  IDE 'deki her pencerenin ayrıntılarının parçası olan ve etkin seçimleri izlemek için kullanılan içerik verileri seçim. Seçim bağlamı aşağıdakilerden oluşur:

- `IVsHierarchy`Proje hiyerarşisinin arabirimine yönelik işaretçi

- Proje öğesinin öğe tanımlayıcısı.

- `ISelectionContainer`Etkin nesneler için özelliklere erişim sağlayan arabirime yönelik işaretçi.

- Öğe değerleri dizisi.

  tek bir COM nesnesinde bulunan bir COM arabirimleri kümesi için bir anlaşma hizmeti. Bir GUID tarafından tanımlanan bir hizmet oluşturduğunuzda, hizmeti yürüten COM arabirimleri kümesini tanımlarsınız. COM nesneleri bir birbirleriyle iletişim kurmak için Hizmetleri kullanır.

  kullanıcının çalıştığı ilgili projelerin çözüm grubu.

  Standart tasarımcı proje türünden bağımsız olarak kullanılabilecek bir tasarlayıcı. Tüm standart tasarımcılarının kayıt defterine kendi Düzenleyici Fabrika bilgilerini girmesi gerekir. Daha sonra, belirli bir uzantıya sahip bir dosya açıldığında IDE, tasarımcı örneğini oluşturabilir. Verilerin bir dosyada kalıcı olması gerekir.

  belirli bir proje türünden bağımsız olarak kullanılabilecek standart düzenleyici düzenleyici. Bu tür düzenleyicilerde kayıt defterine kayıtlı EditorFactory vardır. Bu, IDE 'nin düzenleyiciyi bulmasını ve çağırabilmesini sağlar.

  standart işletim sistemi Düzenleyicisi Visual Studio 'Ya özgü olmayan bir katıştırma. Bu, iyi bilinen Win32 anahtarları kullanılarak kaydedilir (örneğin, Win32 Explorer nasıl çağıracağını bilir). Böyle bir düzenleyici gömülebilir, düzenleyici hala IDE 'deki yerinde görüntülenir. Aksi takdirde, bu tür düzenleyiciler için ayrı bir üst düzey pencere oluşturulur.

  `IVsUserContext`bağlam çantasına bağlı bir nesne için alt bağlam paketi. Nesne, IDE bileşeni içindeki bir seçim için arama anahtar sözcüklerini, **F1** anahtar sözcüklerini ve öznitelikleri barındırır. Alt bağlam örnekleri araç penceresinde bir komut veya bir düzenleyicide anahtar sözcük içerir.

  IDE tarafından uygulanan ve etkin görevlerin bir listesini görüntüleyen görev listesi araç penceresi.

  nesne için metin arabelleği ortak adı `VSTextBuffer` .

  Nesne için metin görünümü ortak adı `VSTextView` .

  Araç üst düzey bileşeni, kalıcı açılan pencere olarak çalışan ve IDE 'nin Kullanıcı arabirimiyle sıkı şekilde çalışan bir bileşendir. Bağımsız en üst düzey bileşenler gibi, araç üst düzey bileşenleri de IDE ile de modlık ve ileti döngüsü hizmetlerini koordine etmelidir.

  üst düzey bileşen bir IDE penceresinin istemci alanı yerine geçici bir üst düzey pencereyi yöneten VSPackage nesnesi. En üst düzey bileşenler, `IOleComponent` boşta kalma süresine erişim gibi ileti döngüsü hizmetlerinden faydalanmak için arabirimi uygular.

  UI etkin ve şu anda odaklanmış olan bir VSPackage nesnesi etkin.

  Kullanıcı arabirimi hiyerarşisi `IVsUIHierarchy` bir hiyerarşinin görüntülenmesini sağlamak için arabirimi uygulayan BIR com nesnesi. UI hiyerarşisi penceresi `ISelectionContainer` Özellikler penceresi güncelleştirmek için arabirimi uygular; isterseniz diğer proje türü pencereler bu uygulamayı kullanabilir.

  VSCT Visual Studio komut tablosu. . Vsct dosyası, XML biçimindeki menülerin, araç çubuklarının ve komutların yerleşimi ve davranışları hakkında bilgiler içerir.

  VSPackage aşağıdaki öğelerden bir veya daha fazlasını katkıdan, Visual Studio IDE 'yi genişleten yüklenebilir bir yazılım parçasıdır: Kullanıcı arabirimi, hizmetler, proje türleri veya düzenleyici/tasarımcı. VSPackage, arabirimi uygulayan bir COM nesnesinden `IVsPackage` ve seçimi ve diğer özellikleri desteklemek için diğer arabirimleri uygulayan bir veya daha fazla com nesnesi içerir. Ayrıca, VSPackage, belirli kayıt gereksinimlerine sahiptir.
