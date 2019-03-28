# Introduction

记录Java知识





for \(String configLocation : mybatisMapperFile\) {    

	    try {   

	        //匹配被修改过的mapper文件，如果存在，则重新加载  

	        //如果想要重新加载全部mapper，可以不匹配  

	        if\(changeResourceNameList.contains\(configLocation\)\){  

	             XMLMapperBuilder xmlMapperBuilder = new XMLMapperBuilder\(

	          		   Resources.getResourceAsStream\(configLocation\),

	          		   configuration,

	          		   configLocation,

	          		   configuration.getSqlFragments\(\)\);    

	             

	             xmlMapperBuilder.parse\(\);    

	             System.out.println\("mapper文件\[" + configLocation + "\]缓存加载成功"\);    

	        }  

	    } catch \(IOException e\) {    

	        System.out.println\("mapper文件\[" + configLocation + "\]不存在或内容格式不对"\);    

	        continue;    

	    }    

	}

