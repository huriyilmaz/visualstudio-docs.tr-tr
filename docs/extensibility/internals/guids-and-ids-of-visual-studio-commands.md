---
title: Visual Studio komutlarının guıd 'leri ve kimlikleri | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamında (ıde) bulunan komutların guıd ve kimlik değerlerini bulmayı öğrenin.
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
ms.openlocfilehash: bcc20cea8db7aa72c1c13ed5cae095ea4c6944298c47f62fcb2d042df9dfb593
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121337935"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio komutlarının guıd 'leri ve kimlikleri
Visual Studio tümleşik geliştirme ortamına (ıde) eklenen komutların guıd ve kimlik değerleri, Visual Studio SDK 'sının bir parçası olarak yüklenen. vsct dosyalarında tanımlanmıştır. Daha fazla bilgi için bkz. [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 *. Vsct* DOSYALARıNDA tanımlanan IDE nesneleriyle çalışma hakkında daha fazla bilgi için bkz. [menüleri ve komutları genişletme](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Komut tanımı bulma
 Visual Studio 1000 'den fazla komutu tanımladığından, bunların tümünü burada listelemek pratik değildir. Bunun yerine, bir komutun tanımını bulmak için aşağıdaki adımları izleyin.

### <a name="to-locate-a-command-definition"></a>Bir komut tanımını bulmak için

1. Visual Studio, *<Visual Studio SDK yükleme yolu \> \\ \VisualStudioIntegration\Common\Inc* klasöründe şu dosyaları açın: *sharedcmddef. vsct*, *shellcmddef. vsct*, *vsdbgcmdused. vsct*, *Venusmenu. vsct*.

    çoğu Visual Studio komut *sharedcmddef. vsct* ve *shellcmddef. vsct* içinde tanımlanmıştır. *VsDbgCmdUsed. vsct* , hata ayıklayıcıya ait komutları tanımlar ve *Venusmenu. vsct* , Web geliştirmeye özgü komutları tanımlar.

2. Komut bir menü öğesi ise, menü öğesinin tam metnini aklınızda yapın. Komut bir araç çubuğunda düğme ise, üzerinde durakladığınızda görüntülenen araç ipucu metnini unutmayın.

3.  + **Bul** iletişim kutusunu açmak için CTRL **F** tuşlarına basın.

4. **Bulunacak** kutusunda, adım 2 ' de not ettiğiniz metni yazın.

5. **Açık belgelerin tümünün** **Bak** kutusunda görüntülendiğini doğrulayın.

6. Düğme öğesinin bölümünde metin seçilene kadar **Sonrakini Bul** düğmesine tıklayın `<Strings>` . [](../../extensibility/button-element.md)

    `<Button>`Komutun içinde göründüğü öğe, komut tanımıdır.

   Komut tanımını bulduğunuz zaman, komutuyla aynı ve değerleri olan bir [Commandyerleştirme öğesi](../../extensibility/commandplacement-element.md) oluşturarak komutun bir kopyasını başka bir menü veya araç çubuğuna koyabilirsiniz `guid` `id` . Daha fazla bilgi için bkz. yeniden [kullanılabilir düğme grupları oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Özel durumlar
 Aşağıdaki durumlarda, menü metni veya araç ipucu metni, komut tanımındaki ile tam olarak eşleşmeyebilir.

- **Dosya** menüsündeki **Yazdır** komutu gibi altı çizili bir karakter içeren menü öğeleri; Örneğin, *P* altı çizili.

     Menü öğesi adlarında ve işareti (&) karakterinin önünde bulunan karakterler altı çizili olarak görüntülenir. Ancak, *. vsct* dosyaları, özel karakterleri göstermek için ve işareti (&) KARAKTERINI kullanan XML dilinde yazılır ve görüntülenecek bir ampersan 'ın *&amp; amp;* olarak yazılması gerekir. Bu nedenle, bir *. vsct* dosyasında **Print** komutu amp olarak görünür *&amp; ; Yazdır*.

- **Kaydet** gibi dinamik metne sahip komutlar \<Current Filename\> ve **son kullanılan dosyalar** listesindeki öğeler gibi dinamik olarak oluşturulan menü öğeleri.

     Dinamik metinde aramanın güvenilir bir yolu yoktur. bunun yerine, [guıd 'leri ve kimlikleri Visual Studio menülerinin ve kimliklerinin](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) [Visual Studio araç çubuklarının](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)kimliklerini inceleyerek istenen komutu barındıran bir grup bulun ve bu grubun kimliği üzerinde arama yapın. Komut tanımı, [ana öğesi](../../extensibility/parent-element.md)olarak grup içermiyorsa, komutun üst öğesini ayarlayan bir öğe *Için SharedCmdPlace. vsct* ve *ShellCmdPlace. vsct* (veya *VsDbgCmdPlace. vsct* ) ' i arayın `<CommandPlacement>` . *SharedCmdPlace. vsct*, *ShellCmdPlace. vsct* ve *VsDbgCmdPlace. vsct* , *\<Visual Studio SDK installation path\> \VisualStudioIntegration\Common\Inc \\* klasöründedir.

## <a name="see-also"></a>Ayrıca bkz.

- [komut tablosu (. vsct) dosyaları Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)
