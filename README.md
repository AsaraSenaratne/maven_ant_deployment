# SSH_SCP_Maven_Ant
Execute SSH and SCP commands in Maven , Ant environment

Create a Maven project and get the pom.xml file generated.
Below code segment helps to make a SSH connection to a remote server using a key file.


      <execution>
	  <id>execute remote script while SSH</id>
	  <phase>package</phase>
	  <goals>
             <goal>run</goal>
          </goals>
          <configuration>
         	    <target>
			<sshexec host="<name of the machine to which the connection should be established. This can be the ip address                           too>" username="ubuntu" trust="true" verbose="true" keyfile="<path of secret key file>" command="<provide linux                         commands. can be seperated with ;>" timeout="2000" failonerror="false"/>
	            </target>
          </configuration>
        </execution>
       
 Below code segment helps to copy a file from one machine to another remote machine.
 
       <execution>
            <id>scp-to-remote</id>
            <phase>package</phase>
            <goals>
                 <goal>run</goal>
            </goals>
            <configuration>
		<target>
		    <scp localFile="${project.basedir}/<file-location>" 
                    remoteToFile="<location of remote machine to which the file should be copied>" verbose="true" 
                    keyfile="<path of secret key file>" trust="true" passphrase=""/>   	
		</target>
             </configuration>
         </execution>
         
  The Execution blocks should go inside "Executions" tag
