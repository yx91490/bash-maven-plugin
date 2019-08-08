# Cli-maven-plugin

### Introduction

A maven plugin passing maven properties to cli script executing, support variables including but not limited to these:

一个支持运行cli脚本的maven插件，可以将maven的变量传递到脚本的环境变量中，支持包括但不限于以下的maven变量：

```

project_version
project_classRealm
project_artifactId
project_activeProfiles
project_repositories
project_pluginRepositories
project_basedir
project_basedir_name
project_basedir_parent
project_basedir_path
project_basedir_totalSpace
project_basedir_freeSpace
project_basedir_usableSpace
project_pluginArtifactRepositories
project_description
project_dependencies
project_artifact
project_artifact_version
project_artifact_artifactId
project_artifact_scope
project_artifact_classifier
project_artifact_artifactHandler
project_artifact_groupId
project_artifact_repository
project_artifact_baseVersion
project_artifact_dependencyConflictId
project_artifact_dependencyTrail
project_artifact_dependencyFilter
project_artifact_versionRange
project_artifact_versionRange_restrictions
project_artifact_versionRange_recommendedVersion
project_artifact_versionRange_recommendedVersion_buildNumber
project_artifact_versionRange_recommendedVersion_incrementalVersion
project_artifact_versionRange_recommendedVersion_majorVersion
project_artifact_versionRange_recommendedVersion_minorVersion
project_artifact_versionRange_recommendedVersion_qualifier
project_artifact_availableVersions
project_artifact_metadataList
project_artifact_downloadUrl
project_artifact_selectedVersion
project_artifact_selectedVersion_buildNumber
project_artifact_selectedVersion_incrementalVersion
project_artifact_selectedVersion_majorVersion
project_artifact_selectedVersion_minorVersion
project_artifact_selectedVersion_qualifier
project_artifact_id
project_artifact_type
project_artifact_file
project_artifact_file_name
project_artifact_file_parent
project_artifact_file_path
project_artifact_file_totalSpace
project_artifact_file_freeSpace
project_artifact_file_usableSpace
project_packaging
project_remotePluginRepositories
project_buildPlugins
project_pluginManagement
project_groupId
project_url
project_remoteProjectRepositories
project_artifacts
project_model
project_model_version
project_model_artifactId
project_model_profiles
project_model_description
project_model_packaging
project_model_groupId
project_model_url
project_model_build
project_model_build_testOutputDirectory
project_model_build_outputDirectory
project_model_build_sourceDirectory
project_model_build_scriptSourceDirectory
project_model_build_testSourceDirectory
project_model_build_extensions
project_model_modelVersion
project_model_inceptionYear
project_model_prerequisites
project_model_ciManagement
project_model_issueManagement
project_model_organization
project_model_scm
project_model_mailingLists
project_model_developers
project_model_contributors
project_model_licenses
project_model_pomFile
project_model_pomFile_name
project_model_pomFile_parent
project_model_pomFile_path
project_model_pomFile_totalSpace
project_model_pomFile_totalSpace
project_model_pomFile_freeSpace
project_model_pomFile_usableSpace
project_model_projectDirectory
project_model_projectDirectory_name
project_model_projectDirectory_parent
project_model_projectDirectory_path
project_model_projectDirectory_totalSpace
project_model_projectDirectory_freeSpace
project_model_projectDirectory_usableSpace
project_model_modelEncoding
project_model_name
project_model_parent
project_model_id
project_build
project_build_testOutputDirectory
project_build_outputDirectory
project_build_sourceDirectory
project_build_scriptSourceDirectory
project_build_testSourceDirectory
project_build_extensions
project_attachedArtifacts
project_distributionManagement
project_dependencyManagement
project_compileSourceRoots
project_testCompileSourceRoots
project_compileClasspathElements
project_testClasspathElements
project_runtimeClasspathElements
project_modelVersion
project_inceptionYear
project_prerequisites
project_ciManagement
project_issueManagement
project_organization
project_scm
project_mailingLists
project_developers
project_contributors
project_testResources
project_licenses
project_artifactMap
project_pluginArtifacts
project_pluginArtifactMap
project_parentArtifact
project_modules
project_remoteArtifactRepositories
project_distributionManagementArtifactRepository
project_injectedProfileIds
project_collectedProjects
project_dependencyArtifacts
project_originalModel
project_originalModel_version
project_originalModel_artifactId
project_originalModel_profiles
project_originalModel_description
project_originalModel_packaging
project_originalModel_groupId
project_originalModel_url
project_originalModel_build
project_originalModel_build_testOutputDirectory
project_originalModel_build_outputDirectory
project_originalModel_build_sourceDirectory
project_originalModel_build_scriptSourceDirectory
project_originalModel_build_testSourceDirectory
project_originalModel_build_extensions
project_originalModel_modelVersion
project_originalModel_inceptionYear
project_originalModel_prerequisites
project_originalModel_ciManagement
project_originalModel_issueManagement
project_originalModel_organization
project_originalModel_scm
project_originalModel_mailingLists
project_originalModel_developers
project_originalModel_contributors
project_originalModel_licenses
project_originalModel_pomFile
project_originalModel_pomFile_name
project_originalModel_pomFile_parent
project_originalModel_pomFile_path
project_originalModel_pomFile_totalSpace
project_originalModel_pomFile_freeSpace
project_originalModel_pomFile_usableSpace
project_originalModel_projectDirectory
project_originalModel_projectDirectory_name
project_originalModel_projectDirectory_parent
project_originalModel_projectDirectory_path
project_originalModel_projectDirectory_totalSpace
project_originalModel_projectDirectory_freeSpace
project_originalModel_projectDirectory_usableSpace
project_originalModel_modelEncoding
project_originalModel_name
project_originalModel_parent
project_originalModel_id
project_managedVersionMap
project_buildExtensions
project_filters
project_projectReferences
project_defaultGoal
project_extensionDependencyFilter
project_scriptSourceRoots
project_compileArtifacts
project_compileDependencies
project_testArtifacts
project_testDependencies
project_runtimeDependencies
project_runtimeArtifacts
project_systemClasspathElements
project_systemArtifacts
project_systemDependencies
project_reporting
project_reporting_plugins
project_reporting_outputDirectory
project_reporting_excludeDefaults
project_reporting_reportPluginsAsMap
project_reportArtifacts
project_reportArtifactMap
project_extensionArtifacts
project_extensionArtifactMap
project_reportPlugins
project_name
project_resources
project_parent
project_properties
project_id
project_file
project_file_name
project_file_parent
project_file_path
project_file_totalSpace
project_file_freeSpace
project_file_usableSpace
```

### Configuration

配置pom.xml文件：

```
<plugin>
	<groupId>io.github.yx91490</groupId>
	<artifactId>cli-maven-plugin</artifactId>
	<version>1.0.0</version>
	<configuration>
		<commands>
			<command>${basedir}/foo.sh a b c</command>
			<command>${basedir}/foo.sh def</command>
		</commands>
	</configuration>
</plugin>
```

### Run

run:

正常运行:

```
mvn cli:exec
```

print maven environment:

打印maven变量:

```
mvn cli:exec --debug
```

maven environment output:

maven变量输出:

```
[DEBUG] env:project_version=1.0.0
[DEBUG] env:project_artifactId=cli-maven-plugin
[DEBUG] env:project_basedir_name=cli-maven-plugin
...
```