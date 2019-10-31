---
title: Visual Studio komutlarının GUID 'Leri ve kimlikleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7670eacc875bf7c5437d9bb92cc1932753093bd
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186645"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio komutlarının GUID 'Leri ve kimlikleri
Visual Studio tümleşik geliştirme ortamında (IDE) bulunan komutların GUID ve KIMLIK değerleri, Visual Studio SDK 'sının bir parçası olarak yüklenen. vsct dosyalarında tanımlanmıştır. Daha fazla bilgi için bkz. [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 *. Vsct* DOSYALARıNDA tanımlanan IDE nesneleriyle çalışma hakkında daha fazla bilgi için bkz. [menüleri ve komutları genişletme](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Komut tanımı bulma
 Visual Studio 1000 'den fazla komut tanımladığından, bunların tümünü burada listelemek pratik değildir. Bunun yerine, bir komutun tanımını bulmak için aşağıdaki adımları izleyin.

### <a name="to-locate-a-command-definition"></a>Bir komut tanımını bulmak için

1. Visual Studio 'da *< Visual STUDIO SDK yükleme yolu\>\VisualStudioIntegration\Common\Inc\\* klasöründe şu dosyaları açın: *SharedCmdDef. vsct*, *ShellCmdDef. vsct*, *VsDbgCmdUsed. vsct*, *Venusmenu. vsct*.

    Çoğu Visual Studio komutu *SharedCmdDef. vsct* ve *ShellCmdDef. vsct*içinde tanımlanmıştır. *VsDbgCmdUsed. vsct* , hata ayıklayıcıya ait komutları tanımlar ve *Venusmenu. vsct* , Web geliştirmeye özgü komutları tanımlar.

2. Komut bir menü öğesi ise, menü öğesinin tam metnini aklınızda yapın. Komut bir araç çubuğunda düğme ise, üzerinde durakladığınızda görüntülenen araç ipucu metnini unutmayın.

3. **Bul** iletişim kutusunu açmak için **CTRL**+**F** tuşlarına basın.

4. **Bulunacak** kutusunda, adım 2 ' de not ettiğiniz metni yazın.

5. **Açık belgelerin tümünün** **Bak** kutusunda görüntülendiğini doğrulayın.

6. [Düğme öğesinin](../../extensibility/button-element.md)`<Strings>` bölümünde metin seçilene kadar **Sonrakini Bul** düğmesine tıklayın.

    Komutun içinde göründüğü `<Button>` öğesi komut tanımıdır.

   Komut tanımını bulduğunuz zaman, komutla aynı `guid` ve `id` değerlerine sahip bir [Commandyerleştirme öğesi](../../extensibility/commandplacement-element.md) oluşturarak komutun bir kopyasını başka bir menü veya araç çubuğuna koyabilirsiniz. Daha fazla bilgi için bkz. yeniden [kullanılabilir düğme grupları oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Özel durumlar
 Aşağıdaki durumlarda, menü metni veya araç ipucu metni, komut tanımındaki ile tam olarak eşleşmeyebilir.

- **Dosya** menüsündeki **Yazdır** komutu gibi altı çizili bir karakter içeren menü öğeleri; Örneğin, *P* altı çizili.

     Menü öğesi adlarında ve işareti (&) karakterinin önünde bulunan karakterler altı çizili olarak görüntülenir. Ancak, *. vsct* dosyaları, özel karakterleri göstermek için ve işareti (&) KARAKTERINI kullanan XML biçiminde yazılır ve görüntülenecek bir ampersan 'ın *&amp;amp;* olarak yazılması gerekir. Bu nedenle, bir *. vsct* dosyasında **Print** komutu *&amp;amp; olarak görünür. Yazdır*.

- \<geçerli dosya adı\>ve dinamik olarak oluşturulan menü öğelerinin (örneğin, **son dosyalar** listesindeki öğeler **) gibi dinamik** metne sahip komutlar.

     Dinamik metinde aramanın güvenilir bir yolu yoktur. Bunun yerine, [Visual Studio menülerinin GUID 'leri ve kimliklerini](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) , [Visual Studio araç çubuklarının GUID 'lerini](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)ve kimliklerini inceleyerek istenen komutu barındıran bir grup bulun ve bu grubun kimliğini arayın. Komut tanımı, [ana öğesi](../../extensibility/parent-element.md)olarak grup içermiyorsa, ' nin üst öğesini ayarlayan bir `<CommandPlacement>` öğesi Için *SharedCmdPlace. vsct* ve *ShellCmdPlace. vsct* (veya *VsDbgCmdPlace. vsct* ) ' ı arayın. komutundaki. *SharedCmdPlace. vsct*, *ShellCmdPlace. vsct*ve *vsdbgcmdplace. vsct* *\<Visual Studio SDK yükleme yolu\>\VisualStudioIntegration\Common\Inc\\* klasöründedir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komut tablosu (. vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)
