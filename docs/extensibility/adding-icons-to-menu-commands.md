---
title: Menü Komutlarına Simge Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4b71f981472451766f526cf62e975e571cf46da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740161"
---
# <a name="add-icons-to-menu-commands"></a>Menü komutlarına simge ekleme
Komutlar hem menülerde hem de araç çubuklarında görünebilir. Araç çubuklarında, bir komutun yalnızca bir simgeyle (yer kazanmak için) görüntülenmesi yaygınken, menülerde genellikle hem simge hem de metinle bir komut görünür.

 Simgeler 16 piksel genişliğinde ve 16 piksel yüksekliğindedir ve 8 bit renk derinliği (256 renk) veya 32 bit renk derinliği (gerçek renk) olabilir. 32 bit renk simgeleri tercih edilir. Simgeler genellikle tek bir bit eşlemde tek bir yatay satırda düzenlenir, ancak birden çok bit eşlemesine izin verilir. Bu bit *eşlemi,.vsct* dosyasında bit haritasında bulunan tek tek simgelerle birlikte bildirilir. Daha fazla ayrıntı için [Bitmaps öğesi](../extensibility/bitmaps-element.md) için başvuruya bakın.

## <a name="add-an-icon-to-a-command"></a>Komuta simge ekleme
 Aşağıdaki yordam, menü komutu ile varolan bir VSPackage projeniz olduğunu varsayar. Bunu nasıl yapacağımı öğrenmek için menü [komutu içeren uzantı oluştur'a](../extensibility/creating-an-extension-with-a-menu-command.md)bakın.

1. Renk derinliği 32 bit olan bir bit eşlemi oluşturun. Bu bitmap 16 piksel yüksekliğinde ve 16 piksel genişliğinde bir kat olmalıdır bu yüzden bir simge her zaman 16 x 16.

     Her simge bit eşlebesine tek bir satırda yan yana yerleştirilir. Her simgede saydamlık yerlerini belirtmek için alfa kanalını kullanın.

     8 bit renk derinliği kullanıyorsanız, saydamlık `RGB(255,0,255)`olarak macenta kullanın. Ancak, 32 bit renk simgeleri tercih edilir.

2. Simge dosyasını VSPackage projenizdeki *Kaynaklar* dizinine kopyalayın. Çözüm **Gezgini'nde,** simgeyi projeye ekleyin. **(Kaynaklar'ı**seçin ve bağlam menüsünde **Öğe** **Ekle'yi**tıklatın ve simge dosyanızı seçin.)

3. Editörde *.vsct* dosyasını açın.

4. `GuidSymbol` **testIcon**adında bir öğe ekleyin. GUID **(Araçlar** > **GUID Oluştur,** **Ardından Kayıt Defteri Biçimi'ni** seçin ve `value` **Kopyala'yı**tıklatın) oluşturun ve öznitelik içine yapıştırın. Sonuç şu şekilde görünmelidir:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Simge `<IDSymbol>` için bir simge ekleyin. Öznitelik `name` simgenin kimliğidir ve varsa `value` şeritteki konumunu gösterir. Sadece bir simge varsa, 1 ekleyin. Sonuç şu şekilde görünmelidir:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Simgeleri `<Bitmap>` içeren `<Bitmaps>` bit eşlemi temsil etmek için *.vsct* dosyasının bölümünde bir oluşturma.

    - `guid` Değeri önceki adımda oluşturduğunuz öğenin `<GuidSymbol>` adına ayarlayın.

    - Değeri bitmap dosyasının göreli yoluna ayarlama (bu durumda **\\ Kaynaklar\><simgesi dosya adı.** `href`

    - `usedList` Değeri daha önce oluşturduğunuz IDSymbol'a ayarlayın. Bu öznitelik, VSPackage'da kullanılacak simgelerin virgülle sınırlı bir listesini belirtir. Listede olmayan simgeler form derlemesi hariç tutulur.

         Bitmap bloğu aşağıdaki gibi görünmelidir:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Varolan `<Button>` öğede, `Icon` öğeyi daha önce oluşturduğunuz GUIDSymbol ve IDSymbol değerlerine ayarlayın. Aşağıda, bu değerlere sahip bir Düğme öğesi örneği verilmiştir:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Simgenizi test edin. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnekte, komutu bulun. Eklediğiniz simgeyi göstermelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
- [VSCT XML şema referansı](../extensibility/vsct-xml-schema-reference.md)
