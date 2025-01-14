---
title: Projelere sınıf diyagramları ekleme (Sınıf Tasarımcısı)
description: sınıfları ve diğer türleri tasarlama, düzenleme ve yeniden düzenleme, C#, Visual Basic veya C++ projenize bir sınıf diyagramı ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/11/2021
ms.topic: how-to
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d8677fea9668269f2440d2bc2745d837808f2fa1
ms.sourcegitcommit: cc8b4e96ec49a8045b6c31a9cdce1caa30c3ab54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2021
ms.locfileid: "132387329"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Nasıl yapılır: projelere sınıf diyagramları ekleme

sınıfları ve diğer türleri tasarlamak, düzenlemek ve yeniden düzenlemek için C#, Visual Basic veya C++ projenize bir sınıf diyagramı ekleyin. Projedeki kodun farklı kısımlarını görselleştirmek için projeye birden çok sınıf diyagramı ekleyin.

Birden çok uygulama arasında kod paylaşan projelerden sınıf diyagramları oluşturamazsınız. UML sınıf diyagramları oluşturmak için bkz. [UML modelleme projeleri ve diyagramları oluşturma](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

## <a name="install-the-class-designer-component"></a>Sınıf Tasarımcısı bileşenini yükler

**Sınıf Tasarımcısı** bileşenini yüklemediyseniz, yüklemek için aşağıdaki adımları izleyin.

1. Windows Başlat menüsü **Visual Studio Yükleyicisi** açın veya **araçlar**'  >  ın menü çubuğundan **araçlar ve özellikler al** ' ı seçerek Visual Studio.

   **Visual Studio Yükleyicisi** açılır.

1. **Ayrı bileşenler** sekmesini seçin ve ardından **kod araçları** kategorisine gidin.

1. **Sınıf Tasarımcısı** seçin ve ardından **Değiştir**' i seçin.

    ::: moniker range="vs-2017"
   ![Visual Studio Yükleyicisi Sınıf Tasarımcısı bileşeninin ekran görüntüsü](media/class-designer-component.png)
   ::: moniker-end
   ::: moniker range="vs-2019"
   :::image type="content" source="media/vs-2019/class-designer-component.png" alt-text="Visual Studio Yükleyicisi Sınıf Tasarımcısı bileşeninin ekran görüntüsü." lightbox="media/vs-2019/class-designer-component.png":::
   ::: moniker-end
   ::: moniker range="vs-2022"
   :::image type="content" source="media/vs-2022/class-designer-component.png" alt-text="Visual Studio Yükleyicisi Sınıf Tasarımcısı bileşeninin ekran görüntüsü." lightbox="media/vs-2022/class-designer-component.png":::
   ::: moniker-end

   **Sınıf Tasarımcısı** bileşen yüklenmeye başlıyor.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Projeye boş bir sınıf diyagramı ekleme

1. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve ardından   >  **Yeni öğe** Ekle ' yi seçin. Ya da **CTRL** + **SHIFT** + **A**'ya basın.

   **Yeni öğe Ekle** iletişim kutusu açılır.

2. Genel **öğeler**  >  **genel**' i genişletin ve ardından şablon listesinden **sınıf diyagramı** ' nı seçin. Visual C++ projeler için, **sınıf diyagramı** şablonunu bulmak Için **yardımcı program** kategorisine bakın.

   > [!NOTE]
   > **Sınıf diyagramı** şablonunu görmüyorsanız, Visual Studio için **Sınıf Tasarımcısı** bileşenini yüklemek için [adımları izleyin](#install-the-class-designer-component) .

   Sınıf diyagramı Sınıf Tasarımcısı açılır ve **Çözüm Gezgini** *. CD* uzantılı bir dosya olarak görünür. **Araç kutusu**' ndan şekilleri ve çizgileri diyagrama sürükleyebilirsiniz.

Birden fazla sınıf diyagramı eklemek için bu yordamdaki adımları yineleyin.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Varolan türlere göre bir sınıf diyagramı ekleyin

**Çözüm Gezgini**, bir sınıf dosyasının bağlam menüsünü açın (sağ tıklayın) ve ardından **sınıf diyagramını görüntüle**' yi seçin.

-veya-

**Sınıf görünümü**, ad alanı veya tür bağlam menüsünü açın ve ardından **sınıf diyagramını görüntüle**' yi seçin.

> [!TIP]
> **Sınıf görünümü** açık değilse, **Görünüm** menüsünden **sınıf görünümü** açın.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Bir sınıf diyagramında tüm projenin içeriğini görüntüleme

**Çözüm Gezgini** veya sınıf görünümü ' de projeye sağ tıklayın ve **görüntüle**' yi seçin ve ardından **sınıf diyagramını görüntüle**' yi seçin.

Otomatik doldurulmuş bir sınıf diyagramı oluşturulur.

> [!IMPORTANT]
> Sınıf Tasarımcısı .NET Core projelerinde kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](how-to-create-types.md)
- [Nasıl yapılır: varolan türleri görüntüleme](how-to-view-existing-types.md)
- [Sınıfları ve türleri tasarlama ve görüntüleme](designing-and-viewing-classes-and-types.md)
