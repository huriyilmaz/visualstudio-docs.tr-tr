---
title: XML Komut Tablosu Tasarlama (. Vsct) Dosya | Microsoft Docs
description: Düğmeler, birleşik giriş kutuları, menüler ve araç çubukları gibi komut öğelerinin düzenini ve görünümünü açıklayan bir XML komut tablosu (.vsct) dosyası tasarlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a3dc6aa48ef15e49928c87baeb913e18048a7e9e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102732"
---
# <a name="design-xml-command-table-vsct-files"></a>XML komut tablosu (.vsct) dosyaları tasarlama
XML komut tablosu (*.vsct*) dosyası, VSPackage için komut öğelerinin düzenini ve görünümünü açıklar. Komut öğeleri düğmeleri, birleşik giriş kutularını, menüleri, araç çubuklarını ve komut öğeleri gruplarını içerir. Bu makalede XML komut tablosu dosyaları, bunların komut öğelerini ve menüleri nasıl etkilediği ve bunların nasıl oluşturulacakları açıklanmıştır.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Komutlar, menüler, gruplar ve .vsct dosyası
 *.vsct dosyaları* komutlar, menüler ve komut gruplarına göre düzenlenmiştir. *.vsct dosyasındaki* XML etiketleri, komut düğmeleri, komut yerleştirme ve bit eşlemler gibi diğer ilişkili öğelerle birlikte bu öğelerin her birini temsil ediyor.

 Paket şablonunu çalıştırarak yeni bir VSPackage ekleyebilirsiniz. Şablon, seçimlere bağlı olarak bir menü komutu, araç penceresi veya özel düzenleyici için gerekli öğeleri içeren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *bir .vsct* dosyası oluşturur. Bu *.vsct* dosyası daha sonra belirli bir VSPackage'ın gereksinimlerini karşılayacak şekilde değiştirilebilir. Bir *.vsct* dosyasını değiştirme örnekleri için bkz. [Menüleri ve komutları genişletme.](../../extensibility/extending-menus-and-commands.md)

 Yeni, boş bir *.vsct dosyası oluşturmak* için [bkz. Nasıl: *.vsct dosyası* oluşturma.](../../extensibility/internals/how-to-create-a-dot-vsct-file.md) Oluşturulduktan sonra, komut öğesi düzenini açıklamak için dosyaya XML öğeleri, öznitelikler ve değerler eklersiniz. Ayrıntılı bir XML şeması için bkz. [VSCT XML şema başvurusu.](../../extensibility/vsct-xml-schema-reference.md)

## <a name="differences-between-ctc-and-vsct-files"></a>.ctc ile .vsct dosyaları arasındaki farklar
 *Bir .vsct* dosyasındaki XML etiketlerinin ardındaki anlamı artık kullanım dışı *olan .ctc* dosya biçimindeki etiketlerle aynı olsa da, bunların uygulaması biraz farklıdır:

- Yeni etiket, araç çubuğundaki dosyalar gibi derlenmiş diğer **\<extern>** *.h* dosyalarına [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başvurabilirsiniz.

- *.vsct dosyaları* **/include** deyimini destekleyene de *.ctc* dosyaları gibi yeni bir öğe **\<import>** de sunar. Fark şudur: **/include** tüm *bilgileri* getirirken **\<import>** yalnızca adları getirir.

- *.ctc dosyaları,* önişlemci yönergelerinizi tanımladığınız bir üst bilgi dosyası gerektirir ancak *.vsct* dosyaları için bir tane gerekli değildir. Bunun yerine, yönergelerinizi .vsct dosyasının en altında yer alan öğelerde **\<Symbol>** bulunan *sembol tablosuna* girin.

- *.vsct* dosyalarında notlar ve hatta resimler gibi herhangi bir bilgiyi eklemenizi **\<Annotation>** sağlayan bir etiket vardır.

- Değerler öğede öznitelik olarak depolanır.

- Komut bayrakları tek tek depolanmış veya yığılmış olabilir.  Ancak IntelliSense, yığılmış komut bayrakları üzerinde çalışmıyor. Komut bayrakları hakkında daha fazla bilgi için [bkz. CommandFlag öğesi.](../../extensibility/command-flag-element.md)

- Bölme açılanları, birleşik girişler vb. gibi birden çok tür belirtebilirsiniz.

- GUID'ler doğrulanmaz.

- Her kullanıcı arabirimi öğesinin, birlikte görüntülenen metni temsil eden bir dizesi vardır.

- Üst isteğe bağlıdır. Atlanırsa, Bilinmeyen *Grup değeri* kullanılır.

- Icon *bağımsız değişkeni* isteğe bağlıdır.

- Bit eşlem bölümü: Bu bölüm *bir .ctc* dosyasındakiyle aynıdır, ancak artık derleme zamanındavsct.exederleyicisi tarafından çekecek Href aracılığıyla *bir* dosya adı belirtebilirsiniz.

- ResID: Eski bit eşlem kaynak kimliği kullanılabilir ve *yine de .ctc dosyalarında olduğu gibi* çalışır.

- HRef: Bit eşlem kaynağı için bir dosya adı belirtmenize olanak sağlayan yeni bir yöntem. Tüm kullanılanları varsayarak Kullanılan bölümünü atlar. Derleyici önce dosya için yerel kaynakları, ardından herhangi bir net paylaşımda ve **/I** anahtarı tarafından tanımlanan tüm kaynakları aratır.

- Tuş bağlama: Artık bir öykünücü belirtmenize gerek yoktur. Bir tane belirtirsiniz, derleyici düzenleyici ve öykünücü aynı olduğunu varsayacak.

- Keychord: Keychord bırakıldı. Yeni biçim *Key1,Mod1,Key2,Mod2'dir.*  Bir karakter, onaltılık veya VK sabiti belirtsiniz.

yeni derleyicisi *vsct.exe* hem *.ctc* hem *de .vsct dosyalarını derler.* Ancak, *ctc.exe* derleyicisi *.vsct* dosyalarını tanımaz veya derlemez.

Mevcut bir *.cto* *dosyasını bir* .vsct dosyasına dönüştürmek içinvsct.exe *derleyicisini kullanabilirsiniz.* Daha fazla bilgi için, [bkz. How to: Create a .vsct file from an existing .cto file](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>.vsct dosya öğeleri
 Komut tablosu aşağıdaki hiyerarşiye ve öğelere sahiptir:

- [CommandTable öğesi:](../../extensibility/commandtable-element.md)VSPackage ile ilişkili tüm komutları, menü gruplarını ve menüleri temsil eder.

- [Extern öğesi:](../../extensibility/extern-element.md).vsct dosyasıyla birleştirmek istediğiniz dış *.h dosyalarına* başvurur.

- [Include öğesi:](../../extensibility/include-element.md).vsct dosyanız ile birlikte derlemek istediğiniz ek üst bilgi *(.h) dosyalarına* başvurur. Bir *.vsct* dosyası, IDE'nin veya başka bir VSPackage'ın sağladığı komutları, menü gruplarını ve menüleri tanımlayan sabitler içeren *.h* dosyalarını içerebilir.

- [Commands öğesi:](../../extensibility/commands-element.md)Yürütülebiliyor tek tek tüm komutları temsil eder. Her komut aşağıdaki dört alt öğeye sahiptir:

- [Menü öğesi:](../../extensibility/menus-element.md)VSPackage'daki tüm menüleri ve araç çubuklarını temsil eder. Menüler, komut gruplarının kapsayıcılarıdır.

- [Groups öğesi:](../../extensibility/groups-element.md)VSPackage'daki tüm grupları temsil eder. Gruplar, tek tek komutların koleksiyonlarıdır.

- [Düğmeler öğesi:](../../extensibility/buttons-element.md)VSPackage'daki tüm komut düğmelerini ve menü öğelerini temsil eder. Düğmeler, komutlarla ilişkilendirilen görsel denetimlerdir.

- [Bit eşlemler](../../extensibility/bitmaps-element.md)öğesi: VSPackage'daki tüm düğmeler için tüm bit eşlemleri temsil eder. Bit eşlemler, bağlama bağlı olarak komut düğmelerinin yanında veya üzerinde görünen resimlerdir.

- [CommandPlacements öğesi:](../../extensibility/commandplacements-element.md)Tek tek komutların VSPackage menülerinde yerleştirilene ek konumları gösterir.

- [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)öğesi: Bir komutun her zaman veya yalnızca belirli bağlamlarda (örneğin, belirli bir iletişim kutusu veya pencere görüntülendiğinde) görüntüleniyor olup olmadığını belirtir. Bu öğe için bir değere sahip menüler ve komutlar yalnızca belirtilen bağlam etkin olduğunda görüntülenir. Varsayılan davranış, komutu her zaman görüntülemektir.

- [KeyBindings öğesi:](../../extensibility/keybindings-element.md)Komutlar için tüm anahtar bağlamalarını belirtir. Başka bir ifadeyle, komutu yürütmek için basıldığında **Ctrl** S gibi bir veya daha fazla tuş bileşimi + **olması gerekir.**

- [UsedCommands öğesi:](../../extensibility/usedcommands-element.md)Belirtilen komut başka bir kod tarafından uygulansa da, geçerli VSPackage etkin olduğunda komut uygulamasını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sağladığını ortama bilgi sağlar.

- [Semboller öğesi:](../../extensibility/symbols-element.md)Pakette yer alan tüm komutlarınız için sembol adlarını ve GUID kimliklerini içerir.

## <a name="vsct-file-design-guidelines"></a>.vsct dosya tasarım yönergeleri
 Bir *.vsct dosyasını başarıyla tasarlamak* için bu yönergeleri izleyin.

- Komutlar yalnızca gruplara, gruplara yalnızca menülere ve menüler ise yalnızca gruplara yer olabilir. IDE'de yalnızca menüler görüntülenir, gruplar ve komutlar görüntülenmez.

- Alt menüler doğrudan bir menüye atanamaz, ancak sırasıyla bir menüye atanmış olan bir gruba atanmaları gerekir.

- Komutlar, alt menüler ve gruplar, tanımlama yönergelerinin üst alanı kullanılarak bir üst öğe grubuna veya menüye atanabilir.

- Komut tablolarını yalnızca yönergelerde üst alanlar aracılığıyla düzenlemek önemli bir sınırlamaya sahiptir. Nesneleri tanımlayan yönergeler yalnızca bir üst bağımsız değişken alır.

- Komutları, grupları veya alt menüleri yeniden kullanmak, nesnenin kendi çifti ile yeni bir örneği oluşturmak için yeni bir yönergenin kullanımını `GUID:ID` gerektirir.

- Her `GUID:ID` çift benzersiz olmalıdır. Bir menüye, araç çubuğuna veya bağlam menüsüne yerleştirilmiş bir komutu yeniden kullanma, arabirim tarafından <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> işleniyor.

- Komutlar ve alt menüler birden çok gruba da atanabilir ve Gruplar, Komutlar öğesi kullanılarak birden çok menüye [atanabilir.](../../extensibility/commands-element.md)

## <a name="vsct-file-notes"></a>.vsct dosya notları
 Bir *.vsct* dosyasında hem derledikten hem de yerel bir uydu DLL'ye yer verdikten sonra herhangi bir değişiklik yapıyorsanız, **/setup /nosetupvstemplatesdevenv.exe çalıştırmanız gerekir.** Bunu yapmak deneysel kayıt defterinde belirtilen VSPackage kaynaklarını yeniden okunma ve yeniden oluşturmak için açıklayan iç [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] veritabanını zorlar.

 Geliştirme sırasında, IDE'de kafa karıştırıcı karışıklığa yol açacak deneysel kayıt defteri kovanını oluşturan ve kaydeden birden çok VSPackage projesi olabilir. Bunu düzeltmek için deneysel kovanı varsayılan ayarlara sıfırlayabilirsiniz. Bu ayar tüm kayıtlı VSPackage'ları ve IDE'de yapmış olduğu tüm değişiklikleri kaldırır. Deneysel kovanı sıfırlamak için CreateExpInstance.exe SDK ile birlikte gelen Visual Studio kullanın. Bu yolu şu şekilde bulabilirsiniz:

 *%PROGRAMFILES(x86)%\Visual Studio \\ \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 **CreateExpInstance /Reset komutunu kullanarak aracı çalıştırın.** Bu aracın deneysel kovandan normal olarak ile yüklenmemiş tüm kayıtlı VSPackage'ları kaldıran olduğunu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../../extensibility/extending-menus-and-commands.md)
