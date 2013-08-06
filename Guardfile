# Guardfile for rest-client project
# More info at https://github.com/guard/guard#readme
#
# 'watch' statements within a guard are additive; in other words, a file that
# matches more than one watch will trigger them all.

guard 'bundler' do
  watch('Gemfile')
  watch('Gemfile.devtools')
  watch(/^.+\.gemspec/)
end

guard :rspec do
  watch('lib/restclient/request.rb')   { 'spec/unit/request2_spec.rb' }
  watch(%r{^lib/restclient/(.+)\.rb$}) { |m| "spec/unit/#{m[1]}_spec.rb" }
  watch(%r{^lib/.+\.rb$})              { 'spec/integration' }
  watch('spec/spec_helper.rb')         { 'spec' }
  watch(%r{^spec/.+_spec\.rb$})
end

guard :rubocop, cli: %w(-c config/rubocop.yml) do
  watch(%r{.+\.rb$})
  watch(%r{config/rubocop.*\.yml$}) { :all }
  watch(%r{(?:.+/)?\.rubocop\.yml$}) { |m| File.dirname(m[0]) }
end
