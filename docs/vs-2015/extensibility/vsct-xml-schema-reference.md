---
title: VSCT XML Şeması Başvurusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e56de828d3b357762da98cde3b9591033c6b5d19
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "64805735"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML Şeması Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Her biri için izin verilen alt öğe ve özniteliklere sahip bir komut tablosu derleyici şeması öğeleri tablosu sağlar.  
  
 XML tabanlı bir komut tablosu yapılandırma (. vsct) dosyası, bir VSPackage 'ın tümleşik geliştirme ortamına (IDE) sağladığı komut öğelerini tanımlar. Bu öğeler menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutularını içerir.  
  
> [!NOTE]
> VSCT derleyicisi,. vsct dosyasında bir Önişlemci çalıştırabilir. Bu genellikle C++ önişlemcisi olduğundan, C++ dosyalarında kullanılan aynı söz dizimine sahip eklemeleri ve makroları tanımlayabilirsiniz. Bunun örnekleri, **Yeni proje** sihirbazının bir VSPackage projesi için oluşturduğu. vsct dosyasında verilmiştir.  
  
## <a name="optional-elements"></a>İsteğe bağlı öğeler  
 Bazı VSCT öğeleri isteğe bağlıdır. Bir `Parent` bağımsız değişken belirtilmemişse, Group_Undefined: 0 kapsanacaktır. Bir `Icon` bağımsız değişken belirtilmemişse, guidOfficeIcon: Msotcıdnoıcon dahil edilir. Bir kısayol tuşu tanımlandığında, genellikle kullanılmamış olan öykünme isteğe bağlıdır.  
  
 Bit eşlem öğeleri, bağımsız değişkende bit eşlem şeridinin konumu belirtilerek derleme zamanında katıştırılabilir `href` . Bit eşlem şeridi, DLL 'nin kaynaklarından ayıklanmak yerine birleştirme sırasında kopyalanır. Bir `href` bağımsız değişken sağlandığında `usedList` bağımsız değişken isteğe bağlıdır ve bit eşlem şeridindeki tüm yuvalar kullanılır olarak kabul edilir.  
  
 Tüm GUID ve KIMLIK değerlerinin sembolik adlar kullanılarak tanımlanması gerekir. Bu adlar, üstbilgi dosyalarında veya VSCT \<Symbols> bölümlerinde tanımlanabilir. Sembolik adların yerel olması, öğeler aracılığıyla dahil olması \<Include> veya öğeler tarafından başvurulması gerekir \<Extern> . Simgesel ad, \<Extern> #define sembol değerinin basit örüntüsünün ardından bir öğede belirtilen üstbilgi dosyasından içeri aktarılır. Bu sembolün daha önce tanımlandığı sürece değer başka bir sembol olabilir. GUID tanımlarının OLE veya C++ biçimi gelmelidir. KIMLIK değerleri, aşağıdaki satırlarda gösterildiği gibi, önünde 0x olan ondalık basamaklar ya da onaltılık basamaklar olabilir:  
  
- {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
- {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8}}  
  
  XML açıklamaları kullanılabilir, ancak gidiş dönüş grafik kullanıcı arabirimi (GUI) araçları tarafından iptal edilebilir. Öğelerin içeriği, \<Annotation> biçiminden bağımsız olarak korunmak üzere garanti edilir.  
  
## <a name="schema-hierarchy"></a>Şema hiyerarşisi  
 Bir. vsct dosyası aşağıdaki ana öğelere sahiptir.  
  
 [CommandTable Öğesi](../extensibility/commandtable-element.md)  
  
 [Extern Öğesi](../extensibility/extern-element.md)  
  
 [Include Öğesi](../extensibility/include-element.md)  
  
 [Define Öğesi](../extensibility/define-element.md)  
  
 [Commands öğesi](../extensibility/commands-element.md)  
  
 [CommandPlacements Öğesi](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints Öğesi](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings Öğesi](../extensibility/keybindings-element.md)  
  
 [UsedCommands Öğesi](../extensibility/usedcommands-element.md)  
  
 [Üst Öğe](../extensibility/parent-element.md)  
  
 [Icon Öğesi](../extensibility/icon-element.md)  
  
 [Dizeler öğesi](../extensibility/strings-element.md)  
  
 [Command Flag Öğesi](../extensibility/command-flag-element.md)  
  
 [Symbols Öğesi](../extensibility/symbols-element.md)  
  
 [Koşullu Öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [VSPackage’larda Komut Yönlendirme](../extensibility/internals/command-routing-in-vspackages.md)
