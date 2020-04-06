---
title: VSCT XML Şema Referans | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697915"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML şema referansı
Komut Tablosu Derleyicisi şema öğeleri tablosunu sağlar, her biri için izin verilen alt öğeler ve öznitelikler.

 XML tabanlı komut tablosu yapılandırması (.vsct) dosyası, vspackage'ın tümleşik geliştirme ortamına (IDE) sağladığı komut öğelerini tanımlar. Bu öğeler menü öğeleri, menüler, araç çubukları ve açılan kutuları içerir.

> [!NOTE]
> VSCT derleyicisi .vsct dosyasında bir önişlemci çalıştırabilir. Bu genellikle C++ önişlemcisi olduğundan, C++ dosyalarında kullanılan sözdizimiyle aynı olan içerir ve makroları tanımlayabilirsiniz. Bunun örnekleri, **Yeni Proje** sihirbazının VSPackage projesi için oluşturduğu .vsct dosyasında verilmiştir.

## <a name="optional-elements"></a>İsteğe bağlı öğeler
 Bazı VSCT öğeleri isteğe bağlıdır. Bir `Parent` bağımsız değişken belirtilmemişse, Group_Undefined:0 ima edilecektir. Bir `Icon` bağımsız değişken belirtilmemişse, guidOfficeIcon:msotcidNoIcon ima edilecektir. Bir kısayol tuşu tanımlandığında, genellikle kullanılmayan öykünme isteğe bağlıdır.

 Bitmap `href` öğeleri, bağımsız değişkendeki biteş şeridinin konumunu belirterek derleme zamanında katıştırılabilir. Bitmap şeridi, DLL'nin kaynaklarından ayıklamak yerine birleştirme sırasında kopyalanır. Bağımsız `href` değişken sağlandığında, `usedList` bağımsız değişken isteğe bağlıdır ve biteş şeritteki tüm yuvalar kullanılmış olarak kabul edilir.

 Tüm GUID ve kimlik değerleri sembolik adlar kullanılarak tanımlanmalıdır. Bu adlar üstbilgi dosyalarında veya \<VSCT Sembolleri> bölümlerinde tanımlanabilir. Sembolik adlar yerel olmalı, \<> öğeleri ni içerme \<yoluyla dahil edilmeli veya Extern> öğeleri tarafından başvurulmalıdır. Sembolik bir \<ad, #define SEMBOL DEĞER'in basit desenini takip ediyorsa, Extern> öğesinde belirtilen bir üstbilgi dosyasından alınır. Bu sembol daha önce tanımlandığı sürece değer başka bir sembol olabilir. GUID tanımları OLE veya C++ biçimini izlemelidir. Kimlik değerleri, aşağıdaki satırlarda gösterildiği gibi, 0x'ten önce gelen ondalık basamaklar veya hexadecimal basamaklar olabilir:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }

  XML yorumları kullanılabilir, ancak gidiş-dönüş grafik kullanıcı arabirimi (GUI) araçları bunları atabilir. Ek açıklama \<> öğelerinin içeriği, biçime bakılmaksızın korunmalıdır.

## <a name="schema-hierarchy"></a>Şema hiyerarşisi
 Bir .vsct dosyasıaşağıdaki ana öğeleri içerir.

- [CommandTable öğesi](../extensibility/commandtable-element.md)

- [Extern elemanı](../extensibility/extern-element.md)

- [Öğe ekle](../extensibility/include-element.md)

- [Öğeyi tanımla](../extensibility/define-element.md)

- [Komutlar öğesi](../extensibility/commands-element.md)

- [Komut Yerleşimleri öğesi](../extensibility/commandplacements-element.md)

- [GörünürlükKısıtlamalar öğesi](../extensibility/visibilityconstraints-element.md)

- [KeyBindings öğesi](../extensibility/keybindings-element.md)

- [UsedCommands öğesi](../extensibility/usedcommands-element.md)

- [Üst öğe](../extensibility/parent-element.md)

- [Simge öğesi](../extensibility/icon-element.md)

- [Dizeleri öğesi](../extensibility/strings-element.md)

- [Komut Bayrağı öğesi](../extensibility/command-flag-element.md)

- [Semboller öğesi](../extensibility/symbols-element.md)

- [Koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VSPackages komut yönlendirme](../extensibility/internals/command-routing-in-vspackages.md)
