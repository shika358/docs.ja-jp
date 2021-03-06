---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fd0d4742a162000d438851cef9c00e21368b7ba1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatereferencegt"></a>&lt;certificateReference&gt;
検索し、証明書ストアで X.509 証明書の検証に使用される設定を指定します。  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<serviceCertificate >  
\<certificateReference >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|storeName|X.509 証明書ストアの名前。 既定値は"My"です。 任意。|  
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 証明書ストアの場所を指定する値。 既定値は、"LocalMachine"です。 任意。|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>を実行する検索の種類を指定する値。 既定値は、「findbysubjectdistinguishedname です」です。 任意。|  
|findValue|X.509 証明書ストアで検索する値。 任意。|  
|isChainIncluded|証明書チェーンを使用して検証を実行するかどうかを指定します。 既定値は"true"です。検証は、証明書チェーンを使用して実行されます。 任意。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|暗号化し、トークン暗号化解除に使用される証明書を構成します。|  
  
## <a name="remarks"></a>コメント  
 `<certificateReference>`要素を検索し、証明書ストアで X.509 証明書の検証に使用される設定を指定します。 子要素として指定した場合、`<serviceCertficate>`の暗号化し、トークン暗号化解除に使用される X.509 証明書の場所と検証の設定を指定します。 `<certificateReference>`要素として表されます、<xref:System.ServiceModel.Configuration.CertificateReferenceElement>クラスです。
