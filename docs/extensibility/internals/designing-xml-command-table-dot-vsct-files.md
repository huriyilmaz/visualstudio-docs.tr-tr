---
title: XML Komut Tablosu Nun Tasarımı (. Vsct) Dosyalar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcd29aee98139bb151c87590b256df6b8370abff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708748"
---
# <a name="design-xml-command-table-vsct-files"></a>XML komut tablosu (.vsct) dosyalarını tasarla
Bir XML komut tablosu (*.vsct*) dosyası, bir VSPackage için komut öğelerinin düzenini ve görünümünü açıklar. Komut öğeleri düğmeleri, açılan kutuları, menüleri, araç çubuklarını ve komut öğeleri gruplarını içerir. Bu makalede, XML komut tablosu dosyaları, komut öğeleri ve menüleri nasıl etkilediği ve bunları nasıl oluşturulacak açıklanmaktadır.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Komutlar, menüler, gruplar ve .vsct dosyası
 *.vsct* dosyaları komutlar, menüler ve komut grupları etrafında düzenlenir. *.vsct* dosyasındaki XML etiketleri, komut düğmeleri, komut yerleşimi ve bit eşlemleri gibi diğer ilişkili öğelerle birlikte bu öğelerin her birini temsil eder.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Paket şablonunu çalıştırarak yeni bir VSPackage oluşturduğunuzda, şablon, seçimlerinize bağlı olarak menü komutu, araç penceresi veya özel düzenleyici için gerekli öğeleri içeren bir *.vsct* dosyası oluşturur. Bu *.vsct* dosyası daha sonra belirli bir VSPackage gereksinimlerini karşılayacak şekilde değiştirilebilir. *.vsct* dosyasının nasıl değiştirilenekadar değiştirilene kadar değiştirilenene örnekler için, [menüleri ve komutları genişlet'e](../../extensibility/extending-menus-and-commands.md)bakın.

 Yeni, boş *.vsct* dosyası oluşturmak [için bkz. *.vsct* ](../../extensibility/internals/how-to-create-a-dot-vsct-file.md) Oluşturulduktan sonra, komut öğesi düzenini açıklamak için dosyaya XML öğeleri, öznitelikleri ve değerler eklersiniz. Ayrıntılı bir XML şeması için [VSCT XML şeması referansına](../../extensibility/vsct-xml-schema-reference.md)bakın.

## <a name="differences-between-ctc-and-vsct-files"></a>.ctc ve .vsct dosyaları arasındaki farklar
 *.vsct* dosyasındaki XML etiketlerinin arkasındaki anlam, şimdi amortismana alınan *.ctc* dosya biçimindeki etiketlerle aynı olsa da, bunların uygulanması biraz farklıdır:

- Yeni ** \<extern>** etiketi, araç çubuğuiçin bu dosyalar gibi derlenecek diğer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *.h* dosyalarına başvuru yaptığınız yerdir.

- *.vsct* dosyaları *,ctc* dosyalarının yaptığı gibi **/include** deyimini desteklerken, yeni ** \<** bir alma>öğesi de içerir. Aradaki fark, **/dahil** *tüm* bilgileri getirirken, ** \<içe aktarma>** yalnızca adları getirir.

- *.ctc* dosyaları önişlemci yönergelerinizi tanımladığınız bir üstbilgi dosyası gerektirirken, *.vsct* dosyaları için bir tane gerekmez. Bunun yerine, yönergelerinizi ** \<** *.vsct* dosyasının alt kısmında bulunan Sembol>öğelerinde bulunan sembol tablosuna yerleştirin.

- *.vsct* dosyaları, ** \<** notlar ve hatta resimler gibi istediğiniz bilgileri gömmenize olanak tanıyan bir Ek açıklama>etiketine sahiptir.

- Değerler maddede öznitelik olarak depolanır.

- Komut bayrakları tek tek veya yığılmış olarak depolanabilir.  Ancak IntelliSense, yığılmış komut bayrakları üzerinde çalışmaz. Komut bayrakları hakkında daha fazla bilgi için [CommandFlag öğesine](../../extensibility/command-flag-element.md)bakın.

- Bölünmüş açılır bırakmalar, kombinasyonlar, vb. gibi birden çok tür belirtebilirsiniz.

- GUID'ler doğrulamaz.

- Her Kullanıcı Arabirimi öğesi, onunla birlikte görüntülenen metni temsil eden bir dize ye sahiptir.

- Üst isteğe bağlıdır. Atlanırsa, *Bilinmeyen Grubu* değeri kullanılır.

- *Simge* bağımsız değişkeni isteğe bağlıdır.

- Bitmap bölümü: Bu bölüm bir *.ctc* dosyasında aynıdır, ancak artık Href üzerinden derleme zamanında *vsct.exe* derleyicisi tarafından çekilecek bir dosya adı belirtebilirsiniz.

- ResID: Eski bitmap kaynak kimliği kullanılabilir ve hala *.ctc* dosyalarındaki gibi çalışır.

- HRef: Bitmap kaynağı için bir dosya adı belirtmenize olanak tanıyan yeni bir yöntem. Tüm kullanılan varsayar, böylece Kullanılan bölümü atlayabilirsiniz. Derleyici önce dosya için yerel kaynakları, daha sonra net paylaşımları ve **/I** anahtarı tarafından tanımlanan kaynakları arayacaktır.

- Anahtar bağlama: Artık bir emülatör belirtmeniz gerekmez. Bir tane belirtirseniz, derleyici düzenleyici ve emülatörün aynı olduğunu varsayacaktır.

- Tuş akoru: Tuş akoru düşürüldü. Yeni format *Key1, Mod1, Key2,Mod2*olduğunu.  Bir karakter, hexadecimal veya VK sabiti belirtebilirsiniz.

Yeni derleyici, *vsct.exe*, hem *.ctc* hem de *.vsct* dosyalarını derler. Ancak eski *ctc.exe* derleyicisi *.vsct* dosyalarını tanımaz veya derlemez.

Varolan bir *.cto* dosyasını *.vsct* dosyasına dönüştürmek için *vsct.exe* derleyicisini kullanabilirsiniz. Daha fazla bilgi için [bkz: Varolan bir .cto dosyasından .vsct dosyası oluşturun.](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)

## <a name="the-vsct-file-elements"></a>.vsct dosya öğeleri
 Komut tablosunda aşağıdaki hiyerarşi ve öğeler vardır:

- [CommandTable öğesi](../../extensibility/commandtable-element.md): VSPackage ile ilişkili tüm komutları, menü gruplarını ve menüleri temsil eder.

- [Extern öğesi](../../extensibility/extern-element.md): *.vsct* dosyasıyla birleştirmek istediğiniz harici .h dosyalarına başvurur.

- [Ekle öğesi](../../extensibility/include-element.md): *.vsct* dosyanızla birlikte derlemek istediğiniz ek üstbilgi (.h) dosyalara başvurur. *Bir .vsct* dosyası, IDE veya başka bir VSPackage'ın sağladığı komutları, menü gruplarını ve menüleri tanımlayan sabitleri içeren *.h* dosyalarını içerebilir.

- [Komutlar öğesi](../../extensibility/commands-element.md): Yürütülebilecek tüm tek tek komutları temsil eder. Her komutun aşağıdaki dört alt öğesi vardır:

- [Menüler öğesi](../../extensibility/menus-element.md): VSPackage'daki tüm menüleri ve araç çubuklarını temsil eder. Menüler komut grupları için kapsayıcılardır.

- [Gruplar öğesi](../../extensibility/groups-element.md): VSPackage'daki tüm grupları temsil eder. Gruplar tek tek komutkoleksiyonlarıdır.

- [Düğmeler öğesi](../../extensibility/buttons-element.md): VSPackage'daki tüm komut düğmelerini ve menü öğelerini temsil eder. Düğmeler komutlarla ilişkilendirilebilen görsel denetimlerdir.

- [Bitmaps öğesi](../../extensibility/bitmaps-element.md): VSPackage'daki tüm düğmelerin bit eşlemlerini temsil eder. Bit eşlemler, içeriğe bağlı olarak komut düğmelerinin yanında veya üzerinde görüntüleyen resimlerdir.

- [CommandPlacements öğesi](../../extensibility/commandplacements-element.md): VSPackage menülerinde tek tek komutların yerleştirilmesi gereken ek konumları gösterir.

- [GörünürlükKısıtlamalar öğesi](../../extensibility/visibilityconstraints-element.md): Bir komutun her zaman görüntülenip görüntülenmediğini veya yalnızca belirli bir iletişim kutusu veya pencerenin görüntülenmesi gibi belirli bağlamlarda görüntülenip görüntülenmediğini belirtir. Bu öğe için bir değere sahip menüler ve komutlar yalnızca belirtilen bağlam etkin olduğunda görüntülenir. Varsayılan davranış, komutu her zaman görüntülemektir.

- [KeyBindings öğesi](../../extensibility/keybindings-element.md): Komutlar için anahtar bağlamaları belirtir. Diğer bir tanesi, **Ctrl**+**S**.

- [UsedCommands öğesi](../../extensibility/usedcommands-element.md): [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Belirtilen komut diğer kod tarafından uygulansa da, geçerli VSPackage etkin olduğunda komut uygulamasını sağladığını çevreye bildirir.

- [Semboller öğesi](../../extensibility/symbols-element.md): Paketteki tüm komutlarınız için sembol adlarını ve GUID adlarını içerir.

## <a name="vsct-file-design-guidelines"></a>.vsct dosya tasarım yönergeleri
 *.vsct* dosyasını başarıyla tasarlamak için aşağıdaki yönergeleri izleyin.

- Komutlar yalnızca gruplar halinde, gruplar yalnızca menülere yerleştirilebilir ve menüler yalnızca gruplar halinde yerleştirilebilir. Sadece menüler Aslında IDE görüntülenir, gruplar ve komutlar değildir.

- Alt menüler doğrudan bir menüye atanamaz, ancak bir menüye sırayla atanan bir gruba atanması gerekir.

- Komutlar, alt menüler ve gruplar, tanımlayıcı yönergelerinin üst alanını kullanarak bir ebeveynlik grubuna veya menüye atanabilir.

- Bir komut tablosunu yalnızca yönergelerde ana alanlar üzerinden düzenlemek önemli bir sınırlamaya sahiptir. Nesneleri tanımlayan yönergeler yalnızca bir üst bağımsız değişken alabilir.

- Komutları, grupları veya alt menüleri yeniden kullanmak, nesnenin kendi `GUID:ID` çiftiyle yeni bir örneğini oluşturmak için yeni bir yönerge kullanılmasını gerektirir.

- Her `GUID:ID` çift benzersiz olmalıdır. Örneğin, bir menüye, araç çubuğuna veya bağlam menüsüne yerleştirilen bir komutun <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> yeniden kullanılması arabirim tarafından işlenir.

- Komutlar ve alt menüler birden çok gruba atanabilir ve gruplar [Komutlar öğesini](../../extensibility/commands-element.md)kullanarak birden çok menüye atanabilir.

## <a name="vsct-file-notes"></a>.vsct dosya notları
 Bir *.vsct* dosyasında hem derleyip yerel bir uydu DLL'ye yerleştirdikten sonra herhangi bir değişiklik yaparsanız, **devenv.exe /setup /nosetupvstemplates**çalıştırmalısınız. Bunu yapmak, deney kayıt defterinde belirtilen VSPackage kaynaklarını ve yeniden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturulmayı açıklayan dahili veritabanını yeniden okumaya zorlar.

 Geliştirme sırasında, deneysel kayıt kovanında ide karışık bir karmaşaya yol açabilecek birden fazla VSPackage projesinin oluşturulması ve kaydedilmesi mümkündür. Bunu düzeltmek için, tüm kayıtlı VSPackages ve IDE yapmış olabilecekleri değişiklikleri kaldırmak için varsayılan ayarlara deneysel kovanı sıfırlayabilirsiniz. Deneysel kovanı sıfırlamak için Visual Studio SDK ile birlikte gelen CreateExpInstance.exe aracını kullanın. Şu anda bulabilirsiniz:

 *%PROGRAMFILES(x86)%\Visual\\\<Studio sürümü> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 **CreateExpInstance /Reset**komutunu kullanarak aracı çalıştırın. Bu aracın deneysel kovandan normalde yüklenmemiş tüm kayıtlı VSPackages kaldırır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../../extensibility/extending-menus-and-commands.md)
