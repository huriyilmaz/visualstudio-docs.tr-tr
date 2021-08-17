---
title: Visual Studio Komutlarının GUID'leri ve | Microsoft Docs
description: Tümleşik geliştirme ortamına (IDE) dahil edilen komutların GUID ve Visual Studio değerlerini nasıl bulasınız?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b06c4b20e4972b8ee697758c1c0b88679f2a37f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063375"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio komutlarının GUID'leri ve kimlikleri
Visual Studio tümleşik geliştirme ortamına (IDE) dahil edilen komutların GUID ve kimlik değerleri, Visual Studio SDK'sı kapsamında yüklü olan .vsct dosyalarında tanımlanır. Daha fazla bilgi için bkz. [IDE tanımlı komutlar, menüler ve gruplar.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 *.vsct* dosyalarında tanımlanan IDE nesneleriyle çalışma hakkında daha fazla bilgi için bkz. [Menüleri ve komutları genişletme.](../../extensibility/extending-menus-and-commands.md)

## <a name="find-a-command-definition"></a>Komut tanımı bulma
 Bu Visual Studio 1000'den fazla komut tanımladığı için, bunların hepsini burada listeleyebilirsiniz. Bunun yerine, bir komutun tanımını bulmak için bu adımları izleyin.

### <a name="to-locate-a-command-definition"></a>Komut tanımını bulmak için

1. Visual Studio'de,<Visual Studio SDK yükleme yolu *\> \\ \VisualStudioIntegration\Common\Inc* klasöründe şu dosyaları açın: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct* *,Tegramenu.vsct*.

    Çoğu Visual Studio komutları *SharedCmdDef.vsct ve* *ShellCmdDef.vsct içinde tanımlanır.* *VsDbgCmdUsed.vsct,* hata ayıklayıcıyla ilgili komutları tanımlar *veEngmenu.vsct* ise Web geliştirmeye özgü komutları tanımlar.

2. Komut bir menü öğesi ise, menü öğesinin tam metnini not seçin. Komut araç çubuğundaki bir düğme ise, araç çubuğunda duraklattığınızda görüntülenen araç ipucu metnini not edin.

3. Bul iletişim kutusunu açmak için **Ctrl** + **F** **tuşlarına** basın.

4. Neyi **bul kutusuna** 2. adımda not not edin.

5. Tüm **Açık Belgeler'in** Look in (Görünüm) kutusunda **görüntülendiğinden emin** olmak.

6. Düğme **öğesinin** bölümünde metin seçilene kadar `<Strings>` Sonrakini Bul [düğmesine tıklayın.](../../extensibility/button-element.md)

    Komutun `<Button>` içinde göründüğü öğe, komut tanımıdır.

   Komut tanımını bulasanız, komutuyla aynı ve değerlerine sahip bir [CommandPlacement](../../extensibility/commandplacement-element.md) öğesi oluşturarak komutun bir kopyasını başka bir menüye veya araç `guid` `id` çubuğuna koyabilirsiniz. Daha fazla bilgi için [bkz. Yeniden kullanılabilir düğme grupları oluşturma.](../../extensibility/creating-reusable-groups-of-buttons.md)

### <a name="special-cases"></a>Özel durumlar
 Aşağıdaki durumlarda menü metni veya araç ipucu metni, komut tanımında yer alan metinle tam olarak eşleşmez.

- P'nin altı çizili olduğu Dosya menüsündeki **Yazdır** komutu gibi altı çizili *karakter* içeren menü öğeleri. 

     Menü öğesi adlarında ve (&) karakteri önünde yer alan karakterler altı çizili olarak görüntülenir. Ancak *. vsct* dosyaları XML biçiminde yazılır ve özel karakterleri belirtmek için ve (&) karakterini kullanır ve bir ve ifadesinin görüntülendiğinde *&amp; amp;* olarak yazmalıdır. Bu nedenle, *bir .vsct dosyasında* Yazdır **komutu** *&amp; amp; yazdırma.*

- Kaydet gibi dinamik metinlere sahip **komutlar** ve Son Dosyalar listesinde yer alan öğeler gibi dinamik olarak \<Current Filename\> oluşturulan **menü** öğeleri.

     Dinamik metinde arama yapmak için güvenilir bir yol yoktur. Bunun yerine, Visual Studio menülerinin GUID'lerine ve [guid'lerine ve](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) [](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)Visual Studio araç çubuklarının kimliklerine bakarak istenen komutu barındıran bir grup bulun ve bu grubun kimliğini bulun. Komut tanımının [Üst](../../extensibility/parent-element.md)öğesi olarak grubu yoksa, komutun üst öğesini ayarlayan bir öğe için *SharedCmdPlace.vsct* ve *ShellCmdPlace.vsct* (veya hata ayıklayıcı komutları *için VsDbgCmdPlace.vsct)* araması `<CommandPlacement>` yapabilirsiniz. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct* ve *VsDbgCmdPlace.vsct* *\<Visual Studio SDK installation path\> \ VisualStudioIntegration\Common\Inc \\ klasöründedir.*

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML şema başvurusu](../../extensibility/vsct-xml-schema-reference.md)
