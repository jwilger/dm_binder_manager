desc "Print all updated documents"
task :print => %w(encyclopedia:print)

namespace :encyclopedia do
  updated_encyclopedia_files = []

  desc "Print updated Encyclopedia PDFs"
  task :print => :update_pdfs do
    unless updated_encyclopedia_files.empty?
      sh "lp -o PageSize=letter -o TonerSaveMode=ON #{updated_encyclopedia_files.join(' ')}"
    end
  end

  task :update_pdfs

  encyclopedia_source_files = Dir.glob('Encyclopedia/**/*.md')
  encyclopedia_template = 'Encyclopedia/encyclopedia_entry.latex'
  encyclopedia_source_files.each do |source_file|
    output_file = 'pdfs/' + source_file.sub(/\.md$/, '.pdf')
    file output_file => source_file do
      sh "mkdir -p #{File.dirname(output_file)}"
      sh "pandoc -o #{output_file} --template=#{encyclopedia_template} #{source_file}"
      updated_encyclopedia_files << output_file
    end
    task :update_pdfs => output_file
  end
end
