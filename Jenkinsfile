pipeline {
    agent any
       
       stage('Unit_Testing') {
            steps {
                 sh '''cd unit_test
                        cmake CMakeLists.txt
                        make
                        ./executeTests'''
            }
        }
        stage('Static_Code_Analysis') {
            steps {
               sh '''cppcheck --enable=all --check-config *.cpp'''
            }
        }
        stage('Build_Project') {
            steps{
                sh '''
                      
                      mkdir $BUILD_NUMBER
                      cd $BUILD_NUMBER 
                      cmake ..
                      make
                      git clone https://github.com/Krishnateja5056/ltts_artifact.git
                      git init
                      git add -A
                      git commit -m "$BUILD_NUMBER"
                      git remote add origin https://Krishnateja5056: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@github.com/Krishnateja5056/ltts_artifact.git
                      git push -f origin master
                      '''
            }
        }
    }

