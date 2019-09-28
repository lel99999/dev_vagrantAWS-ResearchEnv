require 'vagrant-aws'
require 'yaml'

Vagrant.configure('2') do |config|
  config.vm.define "vagrantAWS-Ancillary" do |ancil|
    ancil.vm.box = 'aws-dummy'
    ancil.vm.synced_folder ".", "/vagrant", disabled: true
    ancil.vm.provider 'aws' do |aws,override|
      aws_config = YAML::load_file(File.join(Dir.home, ".aws_secrets"))
      aws.access_key_id = aws_config.fetch("access_key_id")
      aws.secret_access_key = aws_config.fetch("secret_access_key")
      aws.keypair_name = 'vagrantAWS-key'
#       aws.instance_type = "t2.medium"
      aws.instance_type = "t2.small"
#       aws.instance_type = "t2.micro"
#       aws.keypair_name = aws_config.fetch("keypair_name")
      aws.region = 'us-east-1'
      aws.ami = 'ami-0394fe9914b475c53'
#       aws.security_groups = 'sg-08ce8ddb34a878eaf'
#       aws.security_groups = 'vagrant'
#       aws.security_groups = ['default']
      aws.subnet_id = 'subnet-0708d9c83404b507c'
#       aws.tags = {
#         'Name'=> "vagrantAWS-EOD"
#       }

      aws.tags = {
        'Name'=> "vagrantAWS-Ancillary"
      }
      aws.block_device_mapping = [{
        'DeviceName' => '/dev/sda1',
        'Ebs.VolumeSize' => 100,
        'Ebs.DeleteOnTermination' => true,
#         'Ebs.DeleteOnTermination' => false,
        'Ebs.VolumeType' => 'gp2'
#         'Ebs.VolumeType' => 'io1'
#         'Ebs.Iops' => 1000
#         'DeviceName' => AWS_DEVICE_NAME,
#         'Ebs.ValumeSize' => AWS_DEVICE_SIZE,
#         'Ebs.DeleteOnTermination' => false,
#         'Ebs.VolumeType' => AWS_DEVICE_VOL_TYPE,
      }]

      override.ssh.username = "ec2-user"
#       override.ssh.private_key_path = aws_config.fetch("keypair_path")
      override.ssh.private_key_path = '~/.ssh/vagrantAWS-key'
    end
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_ancillaryRH7.yml"
#     ansible.playbook = "deploy_eodrole.yml"
#     ansible.playbook = "deploy_PythonRH7.yml"
#     ansible.groups = {
#       "vagrantAWS" => ["vagrantAWS-Data"]
#     }
      ansible.inventory_path = ".vagrant_hosts"
      ansible.verbose = "true"
    end
  end
  config.vm.define "vagrantAWS-RStudio" do |rstudio|
    rstudio.vm.box = 'aws-dummy'
    rstudio.vm.synced_folder ".", "/vagrant", disabled: true
    rstudio.vm.provider 'aws' do |aws,override|
      aws_config = YAML::load_file(File.join(Dir.home, ".aws_secrets"))
      aws.access_key_id = aws_config.fetch("access_key_id")
      aws.secret_access_key = aws_config.fetch("secret_access_key")
      aws.keypair_name = 'vagrantAWS-key'
#       aws.instance_type = "t2.medium"
      aws.instance_type = "t2.small"
#       aws.instance_type = "t2.micro"
#       aws.keypair_name = aws_config.fetch("keypair_name")
      aws.region = 'us-east-1'
      aws.ami = 'ami-0394fe9914b475c53'
#       aws.security_groups = 'sg-08ce8ddb34a878eaf'
#       aws.security_groups = 'vagrant'
#       aws.security_groups = ['default']
      aws.subnet_id = 'subnet-0708d9c83404b507c'
#       aws.tags = {
#         'Name'=> "vagrantAWS-EOD"
#       }

      aws.tags = {
        'Name'=> "vagrantAWS-RStudio"
      }
      aws.block_device_mapping = [{
        'DeviceName' => '/dev/sda1',
        'Ebs.VolumeSize' => 100,
        'Ebs.DeleteOnTermination' => true,
#         'Ebs.DeleteOnTermination' => false,
        'Ebs.VolumeType' => 'gp2'
#         'Ebs.VolumeType' => 'io1'
#         'Ebs.Iops' => 1000
#         'DeviceName' => AWS_DEVICE_NAME,
#         'Ebs.ValumeSize' => AWS_DEVICE_SIZE,
#         'Ebs.DeleteOnTermination' => false,
#         'Ebs.VolumeType' => AWS_DEVICE_VOL_TYPE,
      }]

      override.ssh.username = "ec2-user"
#       override.ssh.private_key_path = aws_config.fetch("keypair_path")
      override.ssh.private_key_path = '~/.ssh/vagrantAWS-key'
    end
    config.vm.provision "ansible" do |ansible|
#     ansible.playbook = "deploy_ancillaryRH7.yml"
#     ansible.playbook = "deploy_eodrole.yml"
      ansible.playbook = "deploy_rstudio.yml"
#     ansible.groups = {
#       "vagrantAWS" => ["vagrantAWS-Data"]
#     }
      ansible.inventory_path = ".vagrant_hosts"
      ansible.verbose = "true"
    end
  end
  config.vm.define "vagrantAWS-EOD1" do |eod|
    eod.vm.box = 'aws-dummy'
    eod.vm.synced_folder ".", "/vagrant", disabled: true
    eod.vm.provider 'aws' do |aws,override|
      aws_config = YAML::load_file(File.join(Dir.home, ".aws_secrets"))
      aws.access_key_id = aws_config.fetch("access_key_id")
      aws.secret_access_key = aws_config.fetch("secret_access_key")
      aws.keypair_name = 'vagrantAWS-key'
      aws.instance_type = "t2.medium"
#     aws.instance_type = "t2.small"
#     aws.instance_type = "t2.micro"
#     aws.keypair_name = aws_config.fetch("keypair_name")
      aws.region = 'us-east-1'
      aws.ami = 'ami-0394fe9914b475c53'
        aws.security_groups = 'sg-01a0428fe429d1e01'
#       aws.security_groups = 'sg-08ce8ddb34a878eaf'
#       aws.security_groups = 'vagrant'
#       aws.security_groups = ['default']
      aws.subnet_id = 'subnet-0708d9c83404b507c'
#       aws.tags = {
#         'Name'=> "vagrantAWS-EOD"
#       }

      aws.tags = {
        'Name'=> "vagrantAWS-EOD1"
      }
      aws.block_device_mapping = [{
        'DeviceName' => '/dev/sda1',
        'Ebs.VolumeSize' => 100,
        'Ebs.DeleteOnTermination' => true,
#         'Ebs.DeleteOnTermination' => false,
        'Ebs.VolumeType' => 'gp2'
#         'Ebs.VolumeType' => 'io1'
#         'Ebs.Iops' => 1000
#         'DeviceName' => AWS_DEVICE_NAME,
#         'Ebs.ValumeSize' => AWS_DEVICE_SIZE,
#         'Ebs.DeleteOnTermination' => false,
#         'Ebs.VolumeType' => AWS_DEVICE_VOL_TYPE,
      }]

      override.ssh.username = "ec2-user"
#       override.ssh.private_key_path = aws_config.fetch("keypair_path")
      override.ssh.private_key_path = '~/.ssh/vagrantAWS-key'
    end
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_eodrole.yml"
#     ansible.groups = {
#       "vagrantAWS" => ["vagrantAWS-Data"]
#     }
      ansible.inventory_path = ".vagrant_hosts"
      ansible.verbose = "true"
    end
  end
end
