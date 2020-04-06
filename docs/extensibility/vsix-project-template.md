---
title: VSIX Proje Şablonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697929"
---
# <a name="vsix-project-template"></a>VSIX proje şablonu

VSIX Projesi şablonunu kullanarak bir veya daha fazla Visual Studio uzantısını VSIX projesine sarabilir ve paketi [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Web sitesinde yayınlayabilirsiniz.

 VSIX dağıtımı VSPackages, derlemeler, MEF bileşenleri, proje şablonları, öğe şablonları, araç kutusu denetimleri ve özel uzantı türlerini destekler.

> [!NOTE]
> VSIX projelerini kullanmak için Visual Studio SDK'yı yüklemeniz gerekir. Visual Studio SDK hakkında daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

## <a name="where-to-find-the-vsix-project-template"></a>VSIX proje şablonu nerede bulabilirim

VSIX Project şablonu **Yeni Proje** iletişim kutusunda "vsix" arayarak kullanılabilir.  Hem C# hem de Visual Basic sürümü vardır.

> [!TIP]
> .NET Framework 4.5 veya daha yüksek lerinin **Yeni Proje** iletişim kutusunun üst kısmındaki açılır liste kutusunda belirtildiğinden emin olmalısınız.

## <a name="uses-of-the-vsix-project-template"></a>VSIX proje şablonunun kullanımları

VSIX proje şablonu iki ana kullanır:

- Proje şablonlarını, madde şablonlarını ve uzantıları dağıtmak için.

- Birden çok uzantının çıktılarını tek bir dağıtım paketine sarmak için.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Boş bir VSIX projesinde bir uzantıyı paketleme

Varolan bir uzantıyı veya vsix desteği olmayan bir uzantıyı boş bir VSIX projesine sararak paketleyebilirsiniz. Sarılması gereken uzantı [VSIX şeması](../extensibility/vsix-extension-schema-2-0-reference.md)tarafından desteklenen bir tür olmalıdır.

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>VSIX projesi kullanarak uzantıyı paketlemek için

1. Uzantınızı oluşturan projeleri oluşturun.

2. **VSIX Project** şablonu kullanarak bir VSIX projesi oluşturun.

    *Source.extension.vsixmanifest* **Manifest Designer**açılır.

3. **Varlıklar** sekmesinde **Yeni** düğmesini seçin.

    **Yeni Varlık Ekle** iletişim kutusu görüntülenir.

4. **Tür** listesinde, eklenecek uzantı türünü seçin.

5. Geçerli çözüme (örneğin, öğe şablonu veya derlenmiş derleme) dahil olan bir uzantı veya içerik öğesi eklemek için aşağıdaki adımları gerçekleştirin:

   1. **Kaynak** listesinde, **geçerli çözümdeki Bir projeyi**seçin.

   2. **Proje** listesinde uzantının adını seçin.

   3. Bu **klasör kutusuna Göm'e,** varlığı katıştırmak için bir klasörün adını girin ve ardından **Tamam** düğmesini seçin.

6. Geçerli çözüme dahil olmayan bir uzantı veya içerik öğesi eklemek için aşağıdaki adımları gerçekleştirin:

   1. **Kaynak** liste kutusunda, **dosya sisteminde Dosya'yı**seçin.

   2. **Yol** alanında, derlenmiş veya sıkıştırılmış uzantı dosyasına tam yolu girin veya dosyaya göz atmak için **Gözat** düğmesini kullanın.

   3. Bu **klasör kutusuna Göm'e,** varlığı katıştırmak için bir klasörün adını girin ve ardından **Tamam** düğmesini seçin.

7. Paketinizin ek uzantılar içermasını istiyorsanız, bunları aynı şekilde ekleyin.

8. Çözümü derleyin.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX bildirim dosyası, bir [Content_Types]*.xml* dosyası ve projeye eklediğiniz tüm uzantı varlıkları içeren bir *.vsix* dosyası oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [VSIX uzantı şeması 2.0 referans](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)
