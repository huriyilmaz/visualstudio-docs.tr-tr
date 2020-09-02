---
title: GUID 'Ler ve komut kimlikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2feef3cbe72b7eb8db96052236fe483733e22273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538144"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio Komutlarının GUID’leri ve Kimlikleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio tümleşik geliştirme ortamında (IDE) bulunan komutların GUID ve KIMLIK değerleri, Visual Studio SDK 'sının bir parçası olarak yüklenen. vsct dosyalarında tanımlanmıştır. Daha fazla bilgi için bkz. [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 . Vsct dosyalarında tanımlanan IDE nesneleriyle çalışma hakkında daha fazla bilgi için bkz. [genişletme menüleri ve komutları](../../extensibility/extending-menus-and-commands.md).

## <a name="finding-a-command-definition"></a>Komut tanımı bulma
 Visual Studio 1000 'den fazla komut tanımladığından, bunların tümünü burada listelemek pratik değildir. Bunun yerine, bir komutun tanımını bulmak için aşağıdaki adımları izleyin.

#### <a name="to-locate-a-command-definition"></a>Bir komut tanımını bulmak için

1. Visual Studio 'da, *Visual STUDIO SDK yükleme yolu*\VisualStudioIntegration\Common\Inc\ klasöründe şu dosyaları açın: SharedCmdDef. vsct, ShellCmdDef. vsct, VsDbgCmdUsed. vsct, Venusmenu. vsct.

    Çoğu Visual Studio komutu SharedCmdDef. vsct ve ShellCmdDef. vsct içinde tanımlanmıştır. VsDbgCmdUsed. vsct, hata ayıklayıcıya ait komutları tanımlar ve Venusmenu. vsct, Web geliştirmeye özgü komutları tanımlar.

2. Komut bir menü öğesi ise, menü öğesinin tam metnini aklınızda yapın. Komut bir araç çubuğunda düğme ise, üzerinde durakladığınızda görüntülenen araç ipucu metnini unutmayın.

3. **Bul** iletişim kutusunu açmak için CTRL + F tuşlarına basın.

4. **Bulunacak** kutusunda, adım 2 ' de not ettiğiniz metni yazın.

5. **Açık belgelerin tümünün** **Bak** kutusunda görüntülendiğini doğrulayın.

6. Düğme öğesinin bölümünde metin seçilene kadar **Sonrakini Bul** düğmesine tıklayın `<Strings>` . [Button Element](../../extensibility/button-element.md)

    `<Button>`Komutun içinde göründüğü öğe, komut tanımıdır.

   Komut tanımını bulduğunuz zaman, komutuyla aynı ve değerleri olan bir [Commandyerleştirme öğesi](../../extensibility/commandplacement-element.md) oluşturarak komutun bir kopyasını başka bir menü veya araç çubuğuna koyabilirsiniz `guid` `id` . Daha fazla bilgi için bkz. yeniden [kullanılabilir düğme grupları oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Özel Durumlar
 Aşağıdaki durumlarda, menü metni veya araç ipucu metni, komut tanımındaki ile tam olarak eşleşmeyebilir.

- **Dosya** menüsündeki **Yazdır** komutu gibi altı çizili bir karakter içeren menü öğeleri; Örneğin, P altı çizili.

     Menü öğesi adlarında ' & ' karakterinden önce gelen karakterler altı çizili olarak görüntülenir. Ancak,. vsct dosyaları XML dilinde yazılır ve bu, özel karakterleri göstermek için ' & ' karakterini kullanır ve görüntülenecek bir ve ' ' olarak yazılması gerekir &amp; . Bu nedenle, bir. vsct dosyasında **Print** komutu ' Print ' olarak görünür &amp; .

- *Geçerli dosya adını* **Kaydet** gibi dinamik metne sahip komutlar ve **son dosyalar** listesindeki öğeler gibi dinamik olarak oluşturulan menü öğeleri.

     Dinamik metinde aramanın güvenilir bir yolu yoktur. Bunun yerine, [Visual Studio menülerinin GUID 'leri ve kimliklerini](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) , [Visual Studio araç çubuklarının GUID 'lerini](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)ve kimliklerini inceleyerek istenen komutu barındıran bir grup bulun ve bu grubun kimliğini arayın. Komut tanımı, [ana öğesi](../../extensibility/parent-element.md)olarak grup içermiyorsa, komutun üst öğesini ayarlayan bir öğe Için SharedCmdPlace. vsct ve ShellCmdPlace. vsct (veya VsDbgCmdPlace. vsct) ' i arayın `<CommandPlacement>` . SharedCmdPlace. vsct, ShellCmdPlace. vsct, andVsDbgCmdPlace. vsct, *Visual STUDIO SDK yükleme yolu*\VisualStudioIntegration\Common\Inc\ klasöründedir.

## <a name="see-also"></a>Ayrıca Bkz.
 [MenuCommands vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [VSCT XML şema başvurusu](../../extensibility/vsct-xml-schema-reference.md)
