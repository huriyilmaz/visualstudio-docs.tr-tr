---
title: Menü komutlarına simgeler ekleme | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamındaki (IDE) menülerde ve araç çubuklarında görünebilen komutlara simgeler eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 01f159b9f07cd0d530039e0d5707cf38d51610ef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097597"
---
# <a name="add-icons-to-menu-commands"></a>Menü komutlarına simgeler ekleme
Komutlar hem menülerde hem de araç çubuklarında görünebilir. Araç çubuklarında, bir komutun yalnızca bir simgeyle görüntülenmesi (boşluk kazanmak için), bir komutun genellikle bir simge ve metinle birlikte görüntülenmesidir.

 Simgeler 16 piksel genişliğinde 16 piksel yüksekliğinde ve 8 bit renk derinliği (256 renk) ya da 32 bit renk derinliği (gerçek renk) olabilir. 32 bit renk simgeleri tercih edilir. Simgeler, genellikle çoklu bit eşlemlere izin verildiğinde tek bir bit eşlemdeki tek yatay bir satırda düzenlenir. Bu bit eşlem, *. vsct* dosyasında, bit eşlemde bulunan ayrı simgelerle birlikte bildirilmiştir. Daha fazla ayrıntı için bkz. [bit eşlemler öğesi](../extensibility/bitmaps-element.md) başvurusu.

## <a name="add-an-icon-to-a-command"></a>Komuta simge ekleme
 Aşağıdaki yordamda, bir menü komutuyla mevcut bir VSPackage projeniz olduğunu varsaymaktadır. Bunun nasıl yapılacağını öğrenmek için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

1. 32 bitlik renk derinliğine sahip bir bit eşlem oluşturun. Bir simge her zaman 16 x 16 ve bu bit eşlem 16 piksel yüksekliğinde ve 16 piksellik bir kat olmalıdır.

     Her simge, tek bir satırda birbirini izleyen bit eşlemde yer alır. Her bir simgenin saydamlık konumlarını göstermek için alfa kanalını kullanın.

     8 bit renk derinliği kullanıyorsanız, saydamlık olarak Macenta ' i kullanın `RGB(255,0,255)` . Ancak, 32 bit renk simgeleri tercih edilir.

2. Simge dosyasını VSPackage projenizdeki *Resources* dizinine kopyalayın. **Çözüm Gezgini**, simgeyi projeye ekleyin. ( **Kaynakları** seçin ve bağlam menüsünde **Ekle**' ye tıklayın, ardından **Varolan öğe**' ye tıklayın ve simge dosyanızı seçin.)

3. Düzenleyicide *. vsct* dosyasını açın.

4. `GuidSymbol` **Teyapışon** adlı bir öğe ekleyin. Bir GUID oluşturun (**Araçlar**  >  **GUID oluşturun**, ardından **kayıt defteri biçimi** ' ni seçin ve **Kopyala**' ya tıklayın) ve `value` özniteliğe yapıştırın. Sonuç şöyle görünmelidir:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. `<IDSymbol>`Simge için bir ekleyin. `name`Özniteliği SIMGENIN kimliğidir ve `value` varsa Şerit üzerindeki konumunu gösterir. Yalnızca bir simge varsa, 1 ekleyin. Sonuç şöyle görünmelidir:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. `<Bitmap>` `<Bitmaps>` Simgeleri içeren bit eşlemi temsil etmek için *. vsct* dosyasının bölümünde bir oluşturun.

    - Değeri, `guid` `<GuidSymbol>` önceki adımda oluşturduğunuz öğenin adına ayarlayın.

    - `href`Değeri bit eşlem dosyasının göreli yoluna ayarlayın (Bu durumda, **\\<simge dosya adı \>**.

    - `usedList`Değerini daha önce oluşturduğunuz IDSymbol olarak ayarlayın. Bu öznitelik, VSPackage içinde kullanılacak simgelerin virgülle ayrılmış bir listesini belirtir. Listede olmayan simgeler, form derlemesini dışlanıyor.

         Bit eşlem bloğu şuna benzemelidir:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Var olan `<Button>` öğesinde, `Icon` öğesini daha önce oluşturduğunuz GuidSymbol ve IDSymbol değerleri olarak ayarlayın. Bu değerleri içeren bir Button öğesi örneği aşağıda verilmiştir:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Simgenizi test edin. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnekte komutunu bulun. Eklediğiniz simgeyi göstermelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
- [VSCT XML Şeması Başvurusu](../extensibility/vsct-xml-schema-reference.md)
