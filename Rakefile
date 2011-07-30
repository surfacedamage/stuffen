require 'rubygems'
require 'fileutils'
require 'exifr'

IMAGE_TYPES = %w(jpg jpeg)

namespace :stuffen do

  task :setup, [:from, :to] do |task, args|
    $SOURCE_DIR      = args[:from]
    $DESTINATION_DIR = args[:to]
    FileUtils.cd $SOURCE_DIR
  end

  desc "Copy photos to tree structure organized by year"
  task :copy, [:from, :to] => :setup do |task|
    non_year_directories.each do |dir|
      puts "Copying: #{dir}"
      source      = File.join(dir, ".")
      destination = FileUtils.mkdir_p(destination_path(dir))
      FileUtils.cp_r(source, destination)
    end
  end



  def non_year_directories
    Dir.glob("**").reject{ |dir| dir =~ /^\d{4}$/ }
  end

  def folder_image_date(dir)
    images = File.join(dir, "/**/*.{#{IMAGE_TYPES.join(',')}}")
    files  = Dir.glob(images, File::FNM_CASEFOLD)
    jpg_image_date(files.first)
  end

  def jpg_image_date(file)
    EXIFR::JPEG.new(file).date_time
  end

  def destination_path(dir)
    taken_on = folder_image_date(dir)
    File.join($DESTINATION_DIR, taken_on.year.to_s, "#{taken_on.strftime('%Y-%m-%d')} - #{dir}")
  end
end

