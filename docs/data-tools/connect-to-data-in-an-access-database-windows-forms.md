---
title: Bir Access veritabanındaki verilere bağlanma
description: Access veritabanındaki verilere (.mdb dosyası veya .accdb.file) bağlanmayı Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/18/2019
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting
- connecting to data, Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b8280c29649a792839e2bc18a409e76f276b71e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154946"
---
# <a name="connect-to-data-in-an-access-database"></a>Bir Access veritabanındaki verilere bağlanma

Bir Access veritabanına *(.mdb* dosyası veya *.accdb* dosyası) bağlanmak için Visual Studio. Bağlantıyı tanımladığınız veriler Veri Kaynakları **penceresinde** görüntülenir. Buradan tabloları veya görünümleri tasarım yüzeyinize sürükleyebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu yordamları kullanmak için bir Windows Forms veya WPF projesine ve bir Access veritabanına (*.accdb* dosyası) veya access 2000-2003 veritabanına (*.mdb* dosyası) ihtiyacınız vardır. Dosya türünüze karşılık gelen yordamı izleyin.

## <a name="create-a-dataset-for-an-accdb-file"></a>.accdb dosyası için veri kümesi oluşturma

Bağlan yordamı kullanarak Microsoft 365, Access 2013, Access 2010 veya Access 2007 ile oluşturulmuş veritabanlarına erişebilirsiniz.

1. Bir Windows Forms veya WPF uygulama projesini Visual Studio.

2. Veri Kaynakları **penceresini açmak için** Görünüm menüsünde **Diğer** Veri **Kaynakları'Windows**  >  **seçin.**

   ![Diğer Veri Windows Kaynaklarını Görüntüleme](../data-tools/media/viewdatasources.png)

3. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

   Veri **Kaynağı Yapılandırma Sihirbazı** açılır.

4. Veri **Kaynağı** Türü **Seçin sayfasında Veritabanı'ı ve** ardından Sonraki'yi **seçin.**

5. Veritabanı **Modeli Seçin** sayfasında Veri **Kümesi'ne ve** ardından Sonraki'ye **tıklayın.**

6. Yeni bir **veri bağlantısı yapılandırmak için** Veri **Bağlantınızı Seçin** sayfasında Yeni Bağlantı'ya tıklayın.

   Bağlantı **Ekle** iletişim kutusu açılır.

7. Veri **kaynağı Microsoft** Access Veritabanı Dosyası olarak **ayarlanmazsa** Değiştir **düğmesini** seçin.

   Veri **Kaynağını Değiştir iletişim** kutusu açılır. Veri kaynakları listesinde Microsoft Access Veritabanı **Dosyası'ı seçin.** Veri sağlayıcısı **açılan menüsünde,** veri sağlayıcısı için **.NET Framework Veri Sağlayıcısı'OLE DB** ve ardından Tamam'ı **seçin.**

8. Veritabanı **dosya** **adı'nın yanındaki Gözat'ı** seçin, *sonra .accdb dosyanıza* gidin ve Aç'ı **seçin.**

9. Bir kullanıcı adı ve parola girin (gerekirse) ve ardından Tamam'ı **seçin.**

10. Veri **Bağlantınızı** **seçin sayfasında Sonraki'yi** seçin.

    Veri dosyasının geçerli projeniz içinde olmadığını söyleyen bir iletişim kutusuyla karşınıza çıkabilirsiniz. Evet **veya Hayır'ı** **seçin.**

11. Bağlantı **dizesini** **Uygulama Yapılandırması dosyasına kaydet sayfasından Sonraki'yi** seçin.

12. Veritabanı **Nesnelerinizi** seçin **sayfasında Tablolar düğümünü** genişletin.

13. Veri kümenize eklemek istediğiniz tabloları veya görünümleri seçin ve ardından Son'a **seçin.**

    Veri kümesi projenize eklenir ve tablolar ve görünümler Veri Kaynakları **penceresinde** görüntülenir.

## <a name="create-a-dataset-for-an-mdb-file"></a>.mdb dosyası için veri kümesi oluşturma

Bağlan access 2000-2003 ile oluşturulan veritabanlarına aşağıdaki yordamı kullanarak erişebilirsiniz.

1. Bir Windows Forms veya WPF uygulama projesini Visual Studio.

2. Görünüm menüsünde **Diğer** Veri **Kaynakları'Windows**  >  **seçin.**

   ![Diğer Veri Windows Kaynaklarını Görüntüleme](../data-tools/media/viewdatasources.png)

3. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

    Veri **Kaynağı Yapılandırma Sihirbazı** açılır.

4. Veri **Kaynağı** Türü **Seçin sayfasında Veritabanı'ı ve** ardından Sonraki'yi **seçin.**

5. Veritabanı **Modeli Seçin** sayfasında Veri **Kümesi'ne ve** ardından Sonraki'ye **tıklayın.**

6. Yeni bir **veri bağlantısı yapılandırmak için** Veri **Bağlantınızı Seçin** sayfasında Yeni Bağlantı'ya tıklayın.

7. Veri kaynağı Microsoft Access Veritabanı Dosyası **(OLE DB)** değilse, Veri  Kaynağını Değiştir iletişim kutusunu açmak için Değiştir'i seçin ve **Microsoft Access** Veritabanı Dosyası'nın ardından Tamam'ı  **seçin.**

8. Veritabanı **dosyası adı içinde,** bağlanmak istediğiniz *.mdb* dosyasının yolunu ve adını belirtin ve ardından Tamam'ı **seçin.**

   ![Bağlantı Erişimi Veritabanı Dosyası Ekleme](../data-tools/media/add-connection-access-db.png)

9. Veri **Bağlantınızı** **seçin sayfasında Sonraki'yi** seçin.

10. Bağlantı **dizesini** **Uygulama Yapılandırması dosyasına kaydet sayfasından Sonraki'yi** seçin.

11. Veritabanı **Nesnelerinizi** seçin **sayfasında Tablolar düğümünü** genişletin.

12. Veri kümenize istediğiniz tabloları veya görünümleri seçin ve ardından Son'a **seçin.**

    Veri kümesi projenize eklenir ve tablolar ve görünümler Veri Kaynakları **penceresinde** görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar

Yeni oluşturduğunuz veri kümesi, Veri Kaynakları **penceresinde** kullanılabilir. Artık aşağıdaki görevlerden herhangi birini gerçekleştirebilirsiniz:

- Veri Kaynakları penceresinde öğeleri **seçin ve** form veya tasarım yüzeyinize sürükleyin (bkz. [Windows Forms](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) denetimlerini Visual Studio veya WPF veri [bağlamaya genel bakış).](/dotnet/desktop-wpf/data/data-binding-overview)

- Veri kümesinde veri **Veri Kümesi Tasarımcısı** nesneleri eklemek veya düzenlemek için veri kaynağını açın.

- Veri kümesinde veri <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> tablolarının veya olayına doğrulama mantığı ekleyin [(bkz. Veri kümelerde verileri doğrulama).](../data-tools/validate-data-in-datasets.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı ekleme](../data-tools/add-new-connections.md)
- [WPF veri bağlamaya genel bakış](/dotnet/framework/wpf/data/data-binding-overview)
- [Windows Form veri bağlama](/dotnet/framework/winforms/data-binding-and-windows-forms)
