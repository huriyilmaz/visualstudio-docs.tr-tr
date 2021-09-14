---
title: Menü Komutlara Simge Ekleme | Microsoft Docs
description: Tümleşik geliştirme ortamında (IDE) hem menülerde hem de araç çubuklarında Visual Studio komutlara simge eklemeyi öğrenin.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c6ffca49ee3b3c89293be9d9bbc18ebf3f1bb0fe
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636473"
---
# <a name="add-icons-to-menu-commands"></a>Menü komutlarına simge ekleme
Komutlar hem menülerde hem de araç çubuklarında görünebilir. Araç çubuklarda bir komutun yalnızca bir simgeyle (alan kazanmak için) görüntülenebilirken, menülerde genellikle hem simge hem de metin ile bir komut görüntülenir.

 Simgeler 16 piksel genişliğinde ve 16 piksel genişliğindedir ve 8 bit renk derinliği (256 renk) veya 32 bit renk derinliği (gerçek renk) olabilir. 32 bit renk simgeleri tercih edilir. Simgeler genellikle tek bir bit eşlem içinde tek bir yatay satırda düzenlenmiştir, ancak birden çok bit eşlem izin verilir. Bu bit eşlem, bit eşlem içinde kullanılabilen tek tek simgelerle birlikte *.vsct* dosyasında bildirildi. Daha fazla ayrıntı için [Bit Eşlemler öğesi](../extensibility/bitmaps-element.md) başvurusuna bakın.

## <a name="add-an-icon-to-a-command"></a>Komuta simge ekleme
 Aşağıdaki yordamda, menü komutuyla var olan bir VSPackage projeniz olduğu varsayıldı. Bunun nasıl olduğunu bulmak için [bkz. Menü komutuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-a-menu-command.md)

1. Renk derinliği 32 bit olan bir bit eşlem oluşturun. Simge her zaman 16 x 16 olur, bu nedenle bu bit eşlem 16 piksel yüksek ve 16 piksel genişliğinde bir kat olmalıdır.

     Her simge, tek bir satırda yanlarına bit eşlem üzerine yerleştirilir. Her simgede saydamlık yerleri belirtmek için alfa kanalını kullanın.

     8 bit renk derinliği kullanıyorsanız saydamlık olarak magenta `RGB(255,0,255)` kullanın. Ancak 32 bit renk simgeleri tercih edilir.

2. Simge dosyasını VSPackage *projenizin* Resources dizinine kopyalayın. Uygulamanın **Çözüm Gezgini** simgesi projeye ekleyin. **(Kaynaklar'ı** seçin ve bağlam menüsünde **Ekle'ye** ve ardından **Mevcut Öğe'ye tıklayın** ve simge dosyanızı seçin.)

3. *.vsct dosyasını* düzenleyicide açın.

4. `GuidSymbol` **testIcon** adına sahip bir öğe ekleyin. GUID oluşturun (**Araçlar**  >  **GUID Oluşturun,** ardından Kayıt Defteri **Biçimi'ni seçin** ve Kopyala'ya tıklayın) ve özniteliğine `value` yapıştırın. Sonuç aşağıdaki gibi görünüyor olmalı:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Simge için `<IDSymbol>` bir ekleyin. özniteliği, `name` simgenin kimliğidir ve varsa `value` şeritte konumunu gösterir. Yalnızca bir simge varsa 1 ekleyin. Sonuç aşağıdaki gibi görünüyor olmalı:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Simgeleri içeren `<Bitmap>` bit `<Bitmaps>` eşlem'i temsil etmek için *.vsct* dosyasının bölümünde bir oluşturun.

    - Değeri, `guid` önceki adımda oluşturduğunuz `<GuidSymbol>` öğenin adıyla ayarlayın.

    - Değeri `href` bit eşlem dosyasının göreli yoluna ayarlayın (bu durumda **Kaynaklar<dosya \\ adı). \>**

    - Değeri `usedList` daha önce oluşturduğunuz IDSymbol olarak ayarlayın. Bu öznitelik, VSPackage'da kullanılacak simgelerin virgülle ayrılmış listesini belirtir. Listede yer alan simgeler form derlemesi dışında tutulacak.

         Bit Eşlem bloğu şu şekilde görüntülenmiş olmalı:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Mevcut `<Button>` öğede, öğesini `Icon` daha önce oluşturduğunuz GUIDSymbol ve IDSymbol değerlerine ayarlayın. Bu değerlere sahip bir Button öğesinin örneği şöyledir:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Simgenizi test etmek. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnekte komutunu bulun. Ekley istediğiniz simgeyi gösterebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
- [VSCT XML şema başvurusu](../extensibility/vsct-xml-schema-reference.md)
