---
title: Kubernetes Köprüsü ile yönetilen kimlik kullanma
ms.technology: vs-azure
ms.date: 04/28/2021
ms.topic: conceptual
description: Kubernetes Köprüsü ile bir AKS kümesinde Azure Active Directory (Azure AD) tarafından yönetilen kimlik kullanmayı öğrenin
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: e4847b25531b48c8200a2620ca3e975f9677c881
ms.sourcegitcommit: 60b7a6159045a44293043a519c8ea6d915bf2c31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/01/2021
ms.locfileid: "108335093"
---
# <a name="use-managed-identity-with-bridge-to-kubernetes"></a>Kubernetes Köprüsü ile yönetilen kimlik kullanma

AKS kümeniz gizli dizi ve kaynaklara erişimi güvenli hale getirmek için [yönetilen kimlik](/azure/active-directory/managed-identities-azure-resources/overview) güvenliği özellikleri kullanıyorsa, Kubernetes Köprüsü, bu özelliklerle çalışabilecek emin olmak için bazı özel yapılandırmalar gerektirir. Yerel yürütmenin ve hata ayıklamanın düzgün bir şekilde güvende olduğundan ve bu, Kubernetes 'e köprüde bazı özel yapılandırmalar gerektirdiğinden emin olmak için bir Azure Active Directory (AD) belirtecinin yerel makineye indirilmesi gerekir. Bu makalede, Kubernetes tarafından yönetilen kimlik kullanan hizmetlerle çalışacak şekilde köprünün nasıl yapılandırılacağı gösterilmektedir.

## <a name="how-to-configure-your-service-to-use-managed-identity"></a>Hizmetinizi yönetilen kimlik kullanacak şekilde yapılandırma

Yerel bir makineyi yönetilen kimlik desteğiyle etkinleştirmek için, *Kuberneteslocalconfig. YAML* dosyasında `enableFeatures` bölümüne ekleyin `ManagedIdentity` . `enableFeatures`Henüz orada değilse, bölümü ekleyin.

```yaml
enableFeatures:
    ManagedIdentity
```

> [!WARNING]
> Azure AD belirtecinin, olası bir güvenlik riski sunan yerel makineye alındığından, üretim kümelerini değil, geliştirme kümeleriyle çalışırken Kubernetes 'e köprü için yalnızca yönetilen kimlik kullandığınızdan emin olun.

Bir *Kuberneteslocalconfig. YAML* dosyanız yoksa bir tane oluşturabilirsiniz; bkz. [nasıl yapılır: köprüyü Kubernetes 'e yapılandırma](configure-bridge-to-kubernetes.md).

## <a name="how-to-fetch-the-azure-active-directory-tokens"></a>Azure Active Directory belirteçlerini getirme

<xref:Azure.Identity.DefaultAzureCredential>Belirteci getirilirken kodda ya da üzerinde bağlı olduğunuzdan emin olmanız gerekir <xref:Azure.Identity.ManagedIdentityCredential> .

Aşağıdaki C# kodu, kullanırken depolama hesabı kimlik bilgilerinin nasıl getirileceği gösterilmektedir `ManagedIdentityCredential` :

```csharp
var credential = new ManagedIdentityCredential(miClientId);
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Aşağıdaki kod, DefaultAzureCredential kullandığınızda depolama hesabı kimlik bilgilerinin nasıl getirileceği gösterilmektedir:

```csharp
var credential = new DefaultAzureCredential();
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Yönetilen kimlik kullanarak diğer Azure kaynaklarına nasıl erişebileceğinizi öğrenmek için [sonraki adımlar](#next-steps) bölümüne bakın.

## <a name="receive-azure-alerts-when-tokens-are-downloaded"></a>Belirteçler indirildikten sonra Azure uyarıları alın

Bir hizmette Kubernetes için köprü kullandığınızda, Azure AD belirteci yerel makineye indirilir. Bu gerçekleştiğinde Azure uyarılarını bilgilendirmeye olanak sağlayabilirsiniz. Bilgi için bkz. [Azure Defender 'ı etkinleştirme](/azure/security-center/enable-azure-defender). Lütfen bir ücret (30 günlük deneme süresinden sonra) olduğunu unutmayın.

## <a name="next-steps"></a>Sonraki adımlar

Kubernetes 'e, yönetilen kimlik kullanan AKS kümenizde çalışacak şekilde köprü yapılandırdığınıza göre, normal olarak hata ayıklaması yapabilirsiniz. Bkz. [-Kubernetes. MD # Connect-to-Cluster-and-Debug-a-Service].

Aşağıdaki öğreticilerden yararlanarak Azure kaynaklarına erişmek için yönetilen tanımla kullanma hakkında daha fazla bilgi edinin:

- [Öğretici: Azure Depolama’ya erişmek için Linux VM sistem tarafından atanan yönetilen kimliği kullanma](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-storage)
- [Öğretici: Azure Data Lake Store'a erişmek için Linux VM sistem tarafından atanan yönetilen kimliği kullanma](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-datalake)
- [Öğretici: Azure Key Vault'a erişmek için Linux VM sistem tarafından atanan yönetilen kimliği kullanma](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-nonaad)

Diğer Azure kaynaklarına erişmek için yönetilen kimlik kullanmanın yanı sıra bu bölümde başka öğreticiler de vardır.

## <a name="see-also"></a>Ayrıca bkz.

[Azure Active Directory](/azure/active-directory/managed-identities-azure-resources/)
