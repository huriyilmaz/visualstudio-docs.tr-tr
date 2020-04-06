---
title: Görsel Stüdyo Komutlarının GUID'leri ve Kılıkları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708249"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio komutlarının GUID'leri ve kılıkları
Visual Studio tümleşik geliştirme ortamında (IDE) yer alan komutların GUID ve kimlik değerleri Visual Studio SDK'nın bir parçası olarak yüklenen .vsct dosyalarında tanımlanır. Daha fazla bilgi için [IDE tanımlı komutlar, menüler ve gruplara](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)bakın.

 *.vsct* dosyalarında tanımlanan IDE nesneleriile nasıl çalışılabilenler hakkında daha fazla bilgi için genişlet [menülerini ve komutlarını](../../extensibility/extending-menus-and-commands.md)görün.

## <a name="find-a-command-definition"></a>Komut tanımı nı bulma
 Visual Studio 1000'den fazla komut tanımladığı için, hepsini burada listelemek pratik değildir. Bunun yerine, komut tanımını bulmak için aşağıdaki adımları izleyin.

### <a name="to-locate-a-command-definition"></a>Komut tanımını bulmak için

1. Visual Studio'da, *Visual Studio SDK yükleme yoluna\><aşağıdaki dosyaları açın\\ \VisualStudioIntegration\Common\Inc* klasörü: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    Çoğu Visual Studio komutları *SharedCmdDef.vsct* ve *ShellCmdDef.vsct*tanımlanır. *VsDbgCmdUsed.vsct* hata ayıklama ile ilgili komutları tanımlar ve *Venusmenu.vsct* Web geliştirmeye özgü komutları tanımlar.

2. Komut bir menü öğesiyse, menü öğesinin tam metnini not edin. Komut bir araç çubuğundaki bir düğmeyse, üzerinde duraklattığınızda görünen araç ipucu metnine dikkat edin.

3. **Bul** iletişim kutusunu açmak için **Ctrl**+**F** tuşuna basın.

4. Neyi **Bul** kutusuna, adım 2'de belirttiğiniz metni yazın.

5. Tüm **Açık Belgelerin** **Bak** kutusunda görüntülendiğini doğrulayın.

6. [Düğme öğesi](../../extensibility/button-element.md) `<Strings>` bölümünde metin seçilene kadar **İleri'yi Bul** düğmesini tıklatın.

    Komutun göründüğü `<Button>` öğe komut tanımıdır.

   Komut tanımını bulduğunuzda, komutla aynı `guid` ve `id` değerlere sahip bir [CommandPlacement öğesi](../../extensibility/commandplacement-element.md) oluşturarak komutun bir kopyasını başka bir menüye veya araç çubuğuna koyabilirsiniz. Daha fazla bilgi için [bkz.](../../extensibility/creating-reusable-groups-of-buttons.md)

### <a name="special-cases"></a>Özel durumlar
 Aşağıdaki durumlarda, menü metni veya araç ipucu metni komut tanımındakiyle tam olarak eşleşmeyebilir.

- *P'nin* altı çizili olduğu **Dosya** menüsündeki **Yazdır** komutu gibi altı çizili bir karakter içeren menü öğeleri.

     Menü öğesi adlarında ampersand (&) karakterinin önünde ki karakterler altı çizili olarak görüntülenir. Ancak, *.vsct* dosyaları özel karakterleri belirtmek için ampersand (&) karakterini kullanan ve görüntülenecek bir amperandın * &amp;amfi*olarak yazılmasını gerektiren XML ile yazılır; Bu nedenle, bir *.vsct* **dosyasında, Yazdırma** komutu * &amp;amfi olarak görünür; Yazdır*.

- Geçerli Dosya Adını\> **Kaydet** \<gibi dinamik metni olan komutlar ve **Son Dosyalar** listesindeki öğeler gibi dinamik olarak oluşturulan menü öğeleri.

     Dinamik metin üzerinde arama yapmanın güvenilir bir yolu yoktur. Bunun yerine, [Visual Studio menülerinin GUI'lerine ve kimliklerine](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) veya Visual [Studio araç çubuklarının GUI'lerine ve kimliklerine](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)danışarak istenen komutu barındıran bir grup bulun ve bu grubun kimliğini arayın. Komut tanımında [Üst öğe](../../extensibility/parent-element.md)olarak grup yoksa, komutun üst öğesini ayarlayan bir `<CommandPlacement>` öğe için *SharedCmdPlace.vsct* ve *ShellCmdPlace.vsct'i* (veya hata ayıklama komutları için *VsDbgCmdPlace.vsct)* arayın. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*ve *VsDbgCmdPlace.vsct* * \<Visual Studio SDK yükleme yolu\>\VisualStudioIntegration\Common\Inc\\ * klasöründe bulunmaktadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML şema referansı](../../extensibility/vsct-xml-schema-reference.md)
