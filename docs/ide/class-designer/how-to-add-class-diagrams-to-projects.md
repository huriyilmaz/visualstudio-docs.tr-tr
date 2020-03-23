---
title: 'Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)'
ms.date: 05/08/2018
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87a6c1e996d820724138b6bf38c6440193a4c26b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588843"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Nasıl yapilir: Projelere sınıf diyagramları ekleme

Sınıfları ve diğer türleri tasarlamak, düzenlemek ve yeniden oluşturmak için C#, Visual Basic veya C++ projenize bir sınıf diyagramı ekleyin. Projede kodun farklı bölümlerini görselleştirmek için projeye birden çok sınıf diyagramı ekleyin.

Birden çok uygulama arasında kod paylaşan projelerden sınıf diyagramları oluşturamazsınız. UML sınıf diyagramları oluşturmak için [bkz.](../../modeling/what-s-new-for-design-in-visual-studio.md)

## <a name="install-the-class-designer-component"></a>Sınıf Tasarımcısı bileşenini yükleme

**Sınıf Tasarımcısı** bileşenini yüklemediyseniz, yüklemek için aşağıdaki adımları izleyin.

1. Visual Studio **Installer'ı** Windows Başlat menüsünden veya Visual Studio'daki menü çubuğundan **Araçlar** > **Al Araçları ve Özellikleri'ni** seçerek açın.

   **Visual Studio Installer** açılır.

1. Bireysel **bileşenleri** sekmesini seçin ve ardından **Kod araçları** kategorisine gidin.

1. **Sınıf Tasarımcısı'nı** seçin ve sonra **Değiştir'i**seçin.

   ![Visual Studio Installer'da Sınıf Tasarımcısı bileşeni](media/class-designer-component.png)

   **Sınıf Tasarımcısı** bileşeni yüklemeye başlar.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Projeye boş sınıf diyagramı ekleme

1. **Çözüm Gezgini'nde,** proje düğümüne sağ tıklayın ve ardından**Yeni Öğe** **Ekle'yi** > seçin. Veya **Ctrl**+**Shift**+**A tuşuna**basın.

   **Yeni Öğe Ekle** iletişim kutusu açılır.

2. **Ortak Öğeler** > **Genel'i**genişletin ve ardından şablon listesinden Sınıf **Diyagramı'nı** seçin. Visual C++ projeleri için **Sınıf Diyagramı** şablonuna bakmak için **Yardımcı Program** kategorisine bakın.

   > [!NOTE]
   > **Sınıf Diyagramı şablonunu** görmüyorsanız, Visual Studio için **Sınıf Tasarımcısı** bileşenini yüklemek için aşağıdaki [adımları izleyin.](#install-the-class-designer-component)

   Sınıf diyagramı Sınıf Tasarımcısı'nda açılır ve **Solution Explorer'da** *.cd* uzantısı olan bir dosya olarak görünür. Şekilleri ve çizgileri **Toolbox'tan**diyagrama sürükleyebilirsiniz.

Birden fazla sınıf diyagramı eklemek için bu yordamdaki adımları yineleyin.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Varolan türleri temel alan sınıf diyagramı ekleme

**Çözüm Gezgini'nde,** sınıf dosyasının bağlam menüsünü açın (sağ tıklatın) ve ardından **Sınıf Diyagramı Görüntüle'yi**seçin.

-veya-

**Sınıf**Görünümü'nde, ad alanı veya tür bağlam menüsünü açın ve ardından **Sınıf Diyagramını Görüntüle'yi**seçin.

> [!TIP]
> **Sınıf Görünümü** açık değilse, **Görünüm** menüsünden **Sınıf Görünümü'nü** açın.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Tam bir projenin içeriğini sınıf diyagramında görüntülemek için

**Çözüm Gezgini** veya Sınıf Görünümü'nde projeyi sağ tıklatın ve **Görünüm'i**seçin, ardından **Sınıf Diyagramını Görüntüle'yi**seçin.

Otomatik doldurulan sınıf diyagramı oluşturulur.

> [!NOTE]
> Sınıf Tasarımcısı .NET Core projelerinde kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl? Sınıf Tasarımcısını kullanarak türleri oluşturma](how-to-create-types.md)
- [Nasıl yapılı: Varolan türleri görüntüleme](how-to-view-existing-types.md)
- [Tasarım ve görünüm sınıfları ve türleri](designing-and-viewing-classes-and-types.md)
