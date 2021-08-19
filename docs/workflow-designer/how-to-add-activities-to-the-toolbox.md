---
title: Araç Kutusuna Etkinlik Ekleme
description: Bu İş Akışı Tasarımcısı, geçerli projenizin içinde ekleyerek veya farklı bir projeden bu etkinliklere başvurarak çözümünüz içindeki Araç Kutusuna etkinlik eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 80535ec883db07e1a431b90ca18e6fbfd53023ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114738"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Nasıl Yapılır: Araç Kutusuna Etkinlik Ekleme

Etkinlikler, çözümünüzde **Araç Kutusuna** birkaç farklı şekilde eklenebilir. Bunları geçerli projenizin içinde ekleyebilir, farklı bir projeden ekleyebilir veya farklı bir derlemeden bu projelere başvuramazsiniz.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Geçerli projenizin içinde bir etkinlik eklemek için

1. Geçerli iş akışı projenize yeni bir özel etkinlik ekleyin. Projenize yeni bir özel etkinlik ekleme hakkında daha fazla bilgi için [bkz. Nasıl kullanılır:](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md)İş Akışına Yeni Öğe Ekleme Project.

2. Etkinliğinize özel mantık ekleyin.

3. Projeyi derleyin. Derleme başarılı olursa, Araç Kutusunda  " " adlı ve bu kategoriye dahil edilen özel etkinliğin yer alan \<*project name*> yeni bir kategori görüntülenir.

    > [!NOTE]
    > Araç kutusu sıfırlanırsa, çözüm yeniden inşa edilmiş olsa bile özel etkinlikler kaldırılır. Araç kutusu sıfırlandıktan sonra özel etkinliklerle yeniden doldurmak için araç kutusunu Visual Studio.

    > [!NOTE]
    > Araç kutusu, verilen bir adın yalnızca bir etkinliğini gösterebilir. Farklı derlemelerden iki etkinlik aynı sınıf adına sahipse, yalnızca biri görüntülenir.

    > [!NOTE]
    > Uygulama etki alanı düzenleyici örnekleri arasında paylaşılır; Statik değişkenler kullanılırsa, düzenleyici örnekleri arasında da paylaşılır. İstenen davranış bu değildir, değişken örneklerini izlemek için bir hizmet kullanılmalıdır. Tasarımcı [içindeki hizmetleri kullanma hakkında bilgi için bkz. ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) Düzenleme Bağlamını Kullanma.

## <a name="to-add-an-activity-from-within-a-different-project"></a>Farklı bir projeden etkinlik eklemek için

1. En az bir iş akışı projesi ve özel etkinlik kitaplığı projesi veya özel etkinlik tanımlayan başka bir iş akışı projesi içeren bir çözüm açın.

2. her iki projeyi de derleme. Derlemeler başarılı olursa, Araç Kutusunda  " " adlı ve bu kategoriye dahil edilen özel etkinliğin yer alan \<*project name*> yeni bir kategori görüntülenir.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Bir derlemeden Araç Kutusuna etkinlik eklemek için

1. Bir iş akışı çözümü açın.

2. Araçlar **menüsünden** Araç Kutusu **Öğelerini Seç'i seçin.**

3. Araç Kutusu **Öğelerini Seç iletişim** kutusunda **System.Activities Bileşenleri**  sekmesini seçin ve ardından eklemek istediğiniz özel etkinliği içeren derlemeye gitmek için Gözat'a tıklayın.

4. Derlemeyi seçin ve Tamam'a **tıklayın.** Özel etkinlik bileşeni bileşen listesine eklenir ve otomatik olarak seçilir.

    1. İletişim **kutusunu kapatmak** için Tamam'a tıklayın.

5. Araç kutusunu görüntülemek için Görünüm **menüsünden Araç** Kutusu'nı seçin. 

6. Özel etkinlik, öğe **eklenmeden önce** odakta olan kategorinin altında Araç Kutusunda görünür. Örneğin, araç kutusu **öğesini** eklemeden önce **Araç** Kutusunda Genel kategorisi seçildiyse, etkinlik Genel kategorisi **altında** görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](developing-applications-with-the-workflow-designer.md)
