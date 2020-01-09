---
title: Bir Access veritabanındaki verilere bağlanma
ms.date: 07/18/2019
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting
- connecting to data, Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: deb163779110c50560787b35ad7744f90f6a7f36
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586867"
---
# <a name="connect-to-data-in-an-access-database"></a>Bir Access veritabanındaki verilere bağlanma

Visual Studio 'Yu kullanarak bir Access veritabanına (bir *. mdb* dosyası ya da *. accdb* dosyası) bağlanabilirsiniz. Bağlantıyı tanımladıktan sonra veriler **veri kaynakları** penceresinde görünür. Buradan, tasarım yüzeyiniz üzerine tabloları veya görünümleri sürükleyebilirsiniz.

## <a name="prerequisites"></a>Prerequisites

Bu yordamları kullanmak için bir Windows Forms veya WPF projesine ve bir erişim veritabanı ( *. accdb* dosyası) ya da erişim 2000-2003 veritabanı ( *. mdb* dosyası) gerekir. Dosya türünüze karşılık gelen yordamı izleyin.

## <a name="create-a-dataset-for-an-accdb-file"></a>. Accdb dosyası için veri kümesi oluşturma

Aşağıdaki yordamı kullanarak Office 365, Access 2013, Access 2010 veya 2007 Access ile oluşturulan veritabanlarına bağlanın.

1. Visual Studio 'da bir Windows Forms veya WPF uygulama projesi açın.

2. **Veri kaynakları** penceresini açmak Için, **Görünüm** menüsünde **diğer Windows** > **veri kaynakları**' nı seçin.

   ![Diğer Windows veri kaynaklarını görüntüleme](../data-tools/media/viewdatasources.png)

3. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

   **Veri kaynağı Yapılandırma Sihirbazı** açılır.

4. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

5. **Veritabanı modeli seçin** sayfasında **veri kümesi** ' ni seçin ve ardından **İleri**' yi seçin.

6. **Veri bağlantınızı seçin** sayfasında yeni **bağlantı** ' yı seçerek yeni bir veri bağlantısı yapılandırın.

   **Bağlantı ekle** iletişim kutusu açılır.

7. **Veri kaynağı** **Microsoft Access veritabanı dosyası (OLE DB)** olarak ayarlanmamışsa, **Değiştir** düğmesini seçin.

   **Veri kaynağını Değiştir** iletişim kutusu açılır. Veri kaynakları listesinde, **Microsoft Access veritabanı dosyası**' nı seçin. **Veri sağlayıcısı** açılır penceresinde **OLE DB için .NET Framework veri sağlayıcısı**' ni seçin ve ardından **Tamam**' ı seçin.

8. **Veritabanı dosya adı**' nın **yanındaki Git ' i seçin ve** ardından *. accdb* dosyanıza gidin ve **Aç**' ı seçin.

9. Bir Kullanıcı adı ve parola girin (gerekliyse) ve ardından **Tamam**' ı seçin.

10. **Veri bağlantınızı seçin** sayfasında **İleri ' yi** seçin.

    Veri dosyasının geçerli projenizde olduğunu söyleyen bir iletişim kutusu alabilirsiniz. **Evet** veya **Hayır**' ı seçin.

11. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri ' yi** seçin.

12. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

13. Veri kümenize dahil etmek istediğiniz tabloları veya görünümleri seçin ve ardından **son**' u seçin.

    Veri kümesi projenize eklenir ve tablolar ve görünümler **veri kaynakları** penceresinde görünür.

## <a name="create-a-dataset-for-an-mdb-file"></a>. Mdb dosyası için veri kümesi oluşturma

Aşağıdaki yordamı kullanarak Access 2000-2003 ile oluşturulan veritabanlarına bağlanın.

1. Visual Studio 'da bir Windows Forms veya WPF uygulama projesi açın.

2. **Görünüm** menüsünde **diğer Windows** > **veri kaynakları**' nı seçin.

   ![Diğer Windows veri kaynaklarını görüntüleme](../data-tools/media/viewdatasources.png)

3. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

    **Veri kaynağı Yapılandırma Sihirbazı** açılır.

4. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

5. **Veritabanı modeli seçin** sayfasında **veri kümesi** ' ni seçin ve ardından **İleri**' yi seçin.

6. **Veri bağlantınızı seçin** sayfasında yeni **bağlantı** ' yı seçerek yeni bir veri bağlantısı yapılandırın.

7. Veri kaynağı **Microsoft Access veritabanı dosyası (OLE DB)** değilse, **Değiştir** ' i seçerek **veri kaynağını Değiştir** Iletişim kutusunu açın ve **Microsoft Access veritabanı dosyası**' nı seçin ve ardından **Tamam**' ı seçin.

8. **Veritabanı dosyası adı**' nda, bağlanmak istediğiniz *. mdb* dosyasının yolunu ve adını belirtin ve ardından **Tamam**' ı seçin.

   ![Bağlantı erişimi veritabanı dosyası Ekle](../data-tools/media/add-connection-access-db.png)

9. **Veri bağlantınızı seçin** sayfasında **İleri ' yi** seçin.

10. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri ' yi** seçin.

11. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

12. Veri kümeniz içinde istediğiniz tabloları veya görünümleri seçin ve ardından **son**' u seçin.

    Veri kümesi projenize eklenir ve tablolar ve görünümler **veri kaynakları** penceresinde görünür.

## <a name="next-steps"></a>Sonraki adımlar

Yeni oluşturduğunuz veri kümesi **veri kaynakları** penceresinde kullanılabilir. Artık aşağıdaki görevlerden herhangi birini gerçekleştirebilirsiniz:

- **Veri kaynakları** penceresinde öğeleri seçin ve bunları formunuza veya tasarım yüzeyine sürükleyin (Windows Forms bkz. [Visual Studio 'da verileri verilere](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) bağlama veya [WPF veri bağlamaya genel bakış](/dotnet/desktop-wpf/data/data-binding-overview)).

- Veri kümesini oluşturan nesneleri eklemek veya düzenlemek için **veri kümesi Tasarımcısı** veri kaynağını açın.

- Veri kümesindeki veri tablolarının <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olayına doğrulama mantığı ekleyin (bkz. [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı ekleme](../data-tools/add-new-connections.md)
- [WPF veri bağlamaya genel bakış](/dotnet/framework/wpf/data/data-binding-overview)
- [Windows Forms veri bağlama](/dotnet/framework/winforms/data-binding-and-windows-forms)
