# ROS Packages

* Software in ROS is organized in _packages_. 
* A package might contain ROS nodes, a ROS-independent library, a dataset, configuration files, a third-party piece of software, or anything else that logically constitutes a useful module. 
* The goal of these packages it to provide this useful functionality in an easy-to-consume manner so that software can be easily reused.
*  In general, ROS packages follow a "Goldilocks" principle: enough functionality to be useful, but not too much that the package is heavyweight and difficult to use from other software.
* Packages are easy to create by hand or with tools like catkin\_create\_pkg. A ROS package is simply a directory descended from ROS\_PACKAGE\_PATH \(see ROS Environment Variables\) that has a package.xml file in it. 
* Packages are the most atomic unit of build and the unit of release. 
* This means that a package is the smallest individual thing you can build in ROS and it is the way software is bundled for release \(meaning, for example, there is one debian package for each ROS package\), respectively.

