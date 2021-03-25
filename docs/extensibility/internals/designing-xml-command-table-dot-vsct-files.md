---
title: XML komut tablosu tasarlama (. Vsct) dosyaları | Microsoft Docs
description: Düğmeler, Birleşik giriş kutuları, menüler ve araç çubukları dahil olmak üzere komut öğelerinin yerleşimini ve görünümünü açıklayan bir XML komut tablosu (. vsct) dosyası tasarlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d6409b5e624cd8596e669f191b2644aaf27a88c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090934"
---
# <a name="design-xml-command-table-vsct-files"></a>XML komut tablosu (. vsct) dosyaları tasarlama
Bir XML komut tablosu (*. vsct*) dosyası, VSPackage için komut öğelerinin yerleşimini ve görünümünü açıklar. Komut öğeleri düğme, Birleşik giriş kutuları, menüler, araç çubukları ve komut öğesi gruplarını içerir. Bu makale, XML komut tablosu dosyalarını, komut öğelerini ve menülerini nasıl etkileyeceğini ve bunların nasıl oluşturulacağını açıklamaktadır.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Komutlar, menüler, gruplar ve. vsct dosyası
 *. Vsct* dosyaları komutlar, menüler ve komut grupları etrafında düzenlenmiştir. *. Vsct* dosyasındaki XML etiketleri, bu öğelerin her birini, komut düğmeleri, komut yerleşimi ve bit eşlemler gibi ilişkili diğer öğelerle birlikte temsil eder.

 Paket şablonunu çalıştırarak yeni bir VSPackage oluşturduğunuzda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , şablon, seçimlerinize bağlı olarak bir menü komutu, araç penceresi veya özel düzenleyici için gerekli öğelerle bir *. vsct* dosyası oluşturur. Bu *. vsct* dosyası, belirli bir VSPackage gereksinimlerini karşılayacak şekilde değiştirilebilir. *. Vsct* dosyasını değiştirme örnekleri için bkz. [menüleri ve komutları genişletme](../../extensibility/extending-menus-and-commands.md).

 Yeni, boş bir *. vsct* dosyası oluşturmak için bkz. [nasıl yapılır: oluşturma *. vsct* dosyası](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Oluşturulduktan sonra, komut öğesi yerleşimini belirtmek için dosyaya XML öğeleri, öznitelikler ve değerler eklersiniz. Ayrıntılı bir XML şeması için bkz. [VSCT XML Schema başvurusu](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>. CTC ve. vsct dosyaları arasındaki farklar
 Bir *. vsct* dosyasındaki XML etiketlerinin arkasındaki anlamı, artık kullanım dışı bırakılmış *. CTC* dosya biçimindeki etiketlerle aynı olsa da, bunların uygulamaları biraz farklıdır:

- Yeni **\<extern>** etiket, derlenen diğer *. h* dosyalarına (örneğin, araç çubuğu için bu dosyalar) başvurulacağını gösterir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- *. Vsct* dosyaları *. CTC* dosyaları olduğu için **/Include** ifadesini destekleirken Ayrıca yeni bir öğe de sunar **\<import>** . Aradaki fark ise, **/Include** , *Tüm* bilgileri sağlar, **\<import>** ancak yalnızca adları gösterir.

- *. CTC* dosyaları, Önişlemci yönerglerinizi tanımladığınız bir üst bilgi dosyası gerektirdiğinden, *. vsct* dosyaları için bir tane gerekli değildir. Bunun yerine, yönerglerinizi **\<Symbol>** *. vsct* dosyasının en altında bulunan öğelerinde bulunan sembol tablosuna yerleştirin.

- *. vsct* dosyaları, **\<Annotation>** notları veya hatta resimler gibi istediğiniz herhangi bir bilgiyi katıştırmanıza olanak tanıyan bir etiket özelliği.

- Değerler öğe üzerinde öznitelikler olarak depolanır.

- Komut bayrakları ayrı ayrı veya yığın halinde depolanabilir.  Ancak IntelliSense, yığın komut bayrakları üzerinde çalışmaz. Komut bayrakları hakkında daha fazla bilgi için bkz. [CommandFlag öğesi](../../extensibility/command-flag-element.md).

- Bölme açılan listeleri, combos vb. gibi birden çok tür belirtebilirsiniz.

- GUID 'Ler doğrulanmaz.

- Her kullanıcı arabirimi öğesinde, onunla birlikte görüntülenen metni temsil eden bir dize vardır.

- Üst öğe isteğe bağlıdır. Atlanırsa, *bilinmeyen değer grubu* kullanılır.

- *Simge* bağımsız değişkeni isteğe bağlıdır.

- Bit eşlem bölümü: Bu bölüm, derleme zamanında *vsct.exe* derleyicisi tarafından çekilecek href aracılığıyla bir dosya adı belirtebileceğiniz bir *. CTC* dosyasındaki ile aynıdır.

- Resd: eski bit eşlem kaynak KIMLIĞI kullanılabilir ve aynı zamanda *. CTC* dosyalarıyla aynı şekilde çalışabilir.

- HRef: bit eşlem kaynağı için bir dosya adı belirtmenizi sağlayan yeni bir yöntem. Bunların tümünün kullanıldığını varsaydığından, kullanılan bölümü atlayabilirsiniz. Derleyici önce dosya için yerel kaynakları, ardından tüm ağ paylaşımlarını ve **/ı** anahtarı tarafından tanımlanan kaynakları arar.

- KeyBinding: artık öykünücü belirtmeniz gerekmez. Bir tane belirtirseniz, derleyici düzenleyicinin ve öykünücüsünün aynı olduğunu varsayacaktır.

- Anahtar Kasası: Keycha bırakılmıştı. Yeni biçim *KEY1, MOD1, key2, MOD2*' dir.  Bir karakter, onaltılı ya da VK sabiti belirtebilirsiniz.

Yeni derleyici, *vsct.exe*, hem *. CTC* hem de *. vsct* dosyalarını derler. Ancak, eski *ctc.exe* derleyicisi *. vsct* dosyalarını tanımaz veya derlemez.

Var olan bir *. CTO* dosyasını bir *. vsct* dosyasına dönüştürmek için *vsct.exe* derleyicisini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: mevcut bir. CTO dosyasından. vsct dosyası oluşturma](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>. Vsct dosya öğeleri
 Komut tablosu aşağıdaki hiyerarşiye ve öğelere sahiptir:

- [CommandTable öğesi](../../extensibility/commandtable-element.md): VSPackage ile ilişkili tüm komutları, menü gruplarını ve menüleri temsil eder.

- [Extern öğesi](../../extensibility/extern-element.md): *. vsct* dosyası ile birleştirmek istediğiniz harici. h dosyalarına başvurur.

- [Include öğesi](../../extensibility/include-element.md): *. vsct* dosyanızdaki birlikte derlemek istediğiniz ek üstbilgi (. h) dosyalarına başvurur. *. Vsct* dosyası, IDE veya başka bir VSPackage 'un sağladığı komutları, menü gruplarını ve menüleri tanımlayan sabitleri içeren *. h* dosyaları içerebilir.

- [Komutlar öğesi](../../extensibility/commands-element.md): yürütülebilecek tüm komutları temsil eder. Her komut aşağıdaki dört alt öğeye sahiptir:

- [Menüler öğesi](../../extensibility/menus-element.md): VSPackage içindeki tüm menüleri ve araç çubuklarını temsil eder. Menüler, komut grupları için kapsayıcılardır.

- [Groups öğesi](../../extensibility/groups-element.md): VSPackage içindeki tüm grupları temsil eder. Gruplar, bireysel komutların koleksiyonlarıdır.

- [Düğmeler öğesi](../../extensibility/buttons-element.md): VSPackage içindeki tüm komut düğmelerini ve menü öğelerini temsil eder. Düğmeler, komutlarla ilişkilendirilebilen görsel denetimlerdir.

- [Bit eşlemler öğesi](../../extensibility/bitmaps-element.md): VSPackage içindeki tüm düğmelerin bit eşlemlerini temsil eder. Bit eşlemler, içeriğe bağlı olarak komut düğmelerinin yanında veya üzerinde görüntülenen resimlerdir.

- [CommandPlacements öğesi](../../extensibility/commandplacements-element.md): bağımsız komutların VSPackage menülerinde aynı olması gereken ek konumları belirtir.

- [Visibilitykısıtlamalar öğesi](../../extensibility/visibilityconstraints-element.md): bir komutun her zaman mı yoksa yalnızca belirli bağlamlarda mı (örneğin, belirli bir iletişim kutusu veya pencere görüntülendiğinde) gösterilip gösterilmeyeceğini belirtir. Bu öğe için bir değere sahip menüler ve komutlar yalnızca belirtilen bağlam etkin olduğunda görüntülenir. Varsayılan davranış, komutu her zaman görüntülemektir.

- [Keybindings öğesi](../../extensibility/keybindings-element.md): komutlar için herhangi bir anahtar bağlama belirtir. Diğer bir deyişle, **CTRL** S gibi komutları yürütmek için basılan bir veya daha fazla tuş birleşimi + .

- [UsedCommands öğesi](../../extensibility/usedcommands-element.md): ortama, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] belirtilen komutun diğer kod tarafından uygulanmasını, ancak geçerli VSPackage etkin olduğunda, komut uygulamasını sağladığını bildirir.

- [Symbols öğesi](../../extensibility/symbols-element.md): paketteki tüm komutlarınız için sembol ADLARıNı ve GUID kimliklerini içerir.

## <a name="vsct-file-design-guidelines"></a>. vsct dosya tasarımı yönergeleri
 Bir *. vsct* dosyasını başarıyla tasarlamak için bu yönergeleri izleyin.

- Komutlar yalnızca gruplara yerleştirilebilecek, gruplar yalnızca menülere yerleştirilebilecek ve menüler yalnızca gruplara yerleştirilebilir. Yalnızca menüler IDE 'de görüntülenir, gruplar ve komutlar değildir.

- Alt menüler bir menüye doğrudan atanamaz, ancak bir menüye atanmış olan bir gruba atanması gerekir.

- Komutlar, alt menüler ve gruplar, kendi tanımlama yönergesinin üst alanı kullanılarak bir üst öğe grubuna veya menüye atanabilir.

- Komut tablosunun yalnızca yönergelerden üst alanlar aracılığıyla düzenlenmesi önemli bir sınırlamaya sahiptir. Nesneleri tanımlayan yönergeler yalnızca bir üst bağımsız değişken alabilir.

- Komutları, grupları veya alt menüleri yeniden kullanmak için yeni bir yönergenin kullanılması gerekir ve bu nesnenin kendi çiftiyle yeni bir örneğini oluşturur `GUID:ID` .

- Her `GUID:ID` çiftin benzersiz olması gerekir. Bir menü, bir araç çubuğu veya bağlam menüsünde yer alan bir komutu yeniden kullanmak arabirim tarafından işlenir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Komutlar ve alt menüler birden çok gruba da atanabilir ve gruplar, [Komutlar öğesi](../../extensibility/commands-element.md)kullanılarak birden çok menüye atanabilir.

## <a name="vsct-file-notes"></a>. vsct dosya notları
 Her iki derleme sonrasında bir *. vsct* dosyasında herhangi bir değişiklik yaparsanız ve bunu yerel BIR uydu dll 'e yerleştirirseniz, **/Setup/nosetupvstemptıvedevenv.exe** çalıştırmalısınız. Bunu yaptığınızda, Deneysel kayıt defterinde belirtilen VSPackage kaynaklarının yeniden yapılandırılması ve yeniden oluşturulması için açıklanan iç veritabanı vardır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Geliştirme sırasında, birden çok VSPackage projesinin oluşturulup, IDE 'de kafa karıştırıcı ile sonuçlanmasına neden olabilecek Deneysel kayıt defteri Hive 'de kaydettirilmesi mümkündür. Bunu yapmak için, tüm kayıtlı VSPackages 'leri ve IDE 'de yapmış olabileceği tüm değişiklikleri kaldırmak üzere deneysel Hive 'yi varsayılan ayarlara sıfırlayabilirsiniz. Deneysel Hive 'yi sıfırlamak için, Visual Studio SDK ile birlikte gelen CreateExpInstance.exe aracını kullanın. Şu adreste bulabilirsiniz:

 *% PROGRAMFILES (x86)% \ Visual Studio \\ \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 **CreateExpInstance/Reset** komutunu kullanarak aracı çalıştırın. Bu aracın, normalde ile yüklenmeyen tüm kayıtlı VSPackages 'leri deneysel Hive 'den kaldırdığından emin unutmayın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları Genişlet](../../extensibility/extending-menus-and-commands.md)
