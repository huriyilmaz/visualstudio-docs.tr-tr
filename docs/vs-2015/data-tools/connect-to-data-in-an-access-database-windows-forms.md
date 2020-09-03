---
title: Access veritabanındaki verilere bağlanma (Windows Forms) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8426e9fcaa29bef36b6701c78d622f6f42fd1171
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651138"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Bir Access veritabanındaki verilere bağlanma (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio kullanarak bir Access veritabanına (bir. mdf dosyası ya da. accdb dosyası) bağlanabilirsiniz. Bağlantıyı tanımladıktan sonra veriler **veri kaynakları** penceresinde görünür. Burada, tabloları veya görünümleri formlarınıza sürükleyebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Bu yordamları kullanmak için, bir Windows Forms uygulama projesine ve bir Access veritabanı (. accdb dosyası) ya da Access 2000 – 2003 veritabanı (. mdb dosyası) gerekir. Dosya türünüze karşılık gelen yordamı izleyin.

## <a name="creating-the-dataset-for-an-accdb-file"></a>. Accdb dosyası için veri kümesi oluşturma
 Aşağıdaki yordamı kullanarak, Access 2013, Office 365, Access 2010 veya 2007 erişimi aracılığıyla oluşturulmuş veritabanlarına bağlanabilirsiniz.

#### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma

1. Veri bağlamak istediğiniz Windows Forms uygulamayı açın.

2. **Görünüm** menüsünde **diğer Windows**  >  **veri kaynakları**' nı seçin.

     ![Diğer Windows veri kaynaklarını görüntüleme](../data-tools/media/viewdatasources.png "ViewDataSources 'lar")

3. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

     ![Yeni veri kaynağı Ekle](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")

4. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

5. **Veritabanı modeli seçin** sayfasında **veri kümesi** ' ni seçin ve ardından **İleri**' yi seçin.

6. **Veri bağlantınızı seçin** sayfasında yeni **bağlantı** ' yı seçerek yeni bir veri bağlantısı yapılandırın.

7. **Veri kaynağını** **OLE DB için .NET Framework veri sağlayıcısı**olarak değiştirin.

     ![Veri Sağlayıcısı OLE DB olarak değiştir](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")

    > [!IMPORTANT]
    > **Microsoft Access veritabanı dosyasının (OLE DB)** veri kaynağı doğru seçim gibi görünse de, bu veri kaynağı türünü yalnızca. mdb veritabanı dosyaları için kullanırsınız.

8. **OLE DB sağlayıcı**' da **Microsoft Office 12,0 Access veritabanı altyapısı OLE DB sağlayıcısı**' nı seçin.

     ![OLE DB sağlayıcısı Microsoft Office 12,0 erişimi](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

9. **Sunucu veya dosya adı**' nda, bağlanmak istediğiniz. accdb dosyasının yolunu ve adını belirtin ve ardından **Tamam**' ı seçin.

    > [!NOTE]
    > Veritabanı dosyasının Kullanıcı adı ve parolası varsa, **Tamam**' ı seçmeden önce bunları belirtin.

10. **Veri bağlantınızı seçin** sayfasında **İleri ' yi** seçin.

11. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri ' yi** seçin.

12. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

13. Veri kümeniz içinde istediğiniz tabloları veya görünümleri seçin ve ardından **son**' u seçin.

     Veri kümesi projenize eklenir ve tablolar ve görünümler **veri kaynakları** penceresinde görünür.

## <a name="creating-the-dataset-for-an-mdb-file"></a>Bir. mdb dosyası için veri kümesi oluşturma
 **Veri kaynağı Yapılandırma Sihirbazı**'Nı çalıştırarak veri kümesini oluşturursunuz.

#### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma

1. Veri bağlamak istediğiniz Windows Forms uygulamayı açın.

2. **Görünüm** menüsünde **diğer Windows**  >  **veri kaynakları**' nı seçin.

     ![Diğer Windows veri kaynaklarını görüntüleme](../data-tools/media/viewdatasources.png "ViewDataSources 'lar")

3. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

4. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

5. **Veritabanı modeli seçin** sayfasında **veri kümesi** ' ni seçin ve ardından **İleri**' yi seçin.

6. **Veri bağlantınızı seçin** sayfasında yeni **bağlantı** ' yı seçerek yeni bir veri bağlantısı yapılandırın.

7. Veri kaynağı **Microsoft Access veritabanı dosyası (OLE DB)** değilse, **Değiştir** ' i seçerek **veri kaynağını Değiştir** Iletişim kutusunu açın ve **Microsoft Access veritabanı dosyası**' nı seçin ve ardından **Tamam**' ı seçin.

8. **Veritabanı dosyası adı**' nda, bağlanmak istediğiniz. mdb dosyasının yolunu ve adını belirtin ve ardından **Tamam**' ı seçin.

     ![Bağlantı erişimi veritabanı dosyası Ekle](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")

9. **Veri bağlantınızı seçin** sayfasında **İleri ' yi** seçin.

10. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri ' yi** seçin.

11. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

12. Veri kümeniz içinde istediğiniz tabloları veya görünümleri seçin ve ardından **son**' u seçin.

     Veri kümesi projenize eklenir ve tablolar ve görünümler **veri kaynakları** penceresinde görünür.

## <a name="security"></a>Güvenlik
 Önemli bilgileri depolamak (örneğin bir parolayı), uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).

## <a name="next-steps"></a>Sonraki Adımlar
 Yeni oluşturduğunuz veri kümesi artık **veri kaynakları** penceresinde kullanılabilir. Artık aşağıdaki görevlerden herhangi birini gerçekleştirebilirsiniz:

- **Veri kaynakları** penceresinde öğeler ' i seçin ve bunları formunuza sürükleyin (bkz. [Visual Studio 'Da verilere veri bağlama Windows Forms denetimleri](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Veri kümesini oluşturan nesneleri eklemek veya düzenlemek için Veri Kümesi Tasarımcısı veri kaynağını açın.

- Veri <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> kümesindeki veri tablolarının veya olayına doğrulama mantığı ekleyin (bkz. [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Ayrıca Bkz.

 Uygulamanızı [Visual Studio 'daki verilere veri bağlama denetimleri](../data-tools/bind-controls-to-data-in-visual-studio.md) [alacak şekilde hazırlama](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [veri](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e) [verileri gözden geçirmeleri](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) doğrulanıyor